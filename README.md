# iPhone向け Whisper Tiny PWA 最小実証版

## 目的
GitHub Pagesで配布し、初回取得後はiPhoneのSafari/PWA上でWhisper Tinyを使った端末内文字起こしを検証する最小構成です。

このテンプレートはGitHub Actionsで公式 whisper.cpp のWebAssemblyデモをビルドし、TinyモデルとPWA用manifest/service workerをまとめてGitHub Pagesへ公開します。

## 公開手順
1. GitHubで新しいPublic Repositoryを作成する。
2. このZIPの中身をRepositoryのルートへアップロードする。
3. Repositoryの Settings > Pages を開く。
4. Sourceで GitHub Actions を選択する。
5. Actionsタブで `Build and deploy Whisper Tiny PWA` の完了を待つ。
6. Pagesに表示されたURLをiPhoneのSafariで開く。

## iPhoneでの確認
1. 初回はWi-Fi接続中にページを開く。
2. Tinyモデルを読み込み、マイク録音テストを行う。
3. Safariの共有 > ホーム画面に追加。
4. 一度PWAを起動した後、機内モードで再起動する。
5. モデルが必要なら最初のオンライン時にローカルモデル `models/ggml-tiny.bin` を選択・読込する。

## 注意
- iPhone Safariのメモリ制限やWASM SIMD対応により、機種・iOS版で性能差があります。
- 公式WASMデモの録音長上限は120秒です。最小実証版では長時間連続会議用途を対象にしていません。
- Service Workerは同一オリジンの取得済みファイルをキャッシュします。初回モデル取得完了前に機内モードにしないでください。
- GitHub Pages公開物は外部から閲覧できます。社内固有情報や音声データをRepositoryへ登録しないでください。
- 音声推論自体はブラウザ内で実行されます。

## 合格条件
- Safariでページが開く
- マイクを許可できる
- Tinyモデルを読み込める
- 30秒程度の音声を日本語文字起こしできる
- ホーム画面追加後、機内モードでもPWAが起動する
