# JKD Day2

## 2020年のコンテナはどうなる？コンテナプラットフォームのこれまでとこれから
- マイクロサービスは組織の問題が絡む
    - システムを組織に合わせて作る日本の企業だと難しい
    - 複数のチーム、アプリケーションインターフェースを決める、チーム内で完結、権限譲渡
- 何がネック
    - マインドセット、カルチャー、技術が揃わないとコンテナ本番導入は難しい
    - 試すのは簡単だが、マネージドで揃えられない場合は運用が難しい（ストレージ、ログ、監視どうする？など
- k8s とそれ以外との差別化
    - k8s が本当に必要か？ほかのプラットフォームの方が合っているケースもある
    - やはりエコシステム、拡張性が強みである
- 今後追うべき技術は？
    - ストレージとサービスメッシュ
    - KubeCon や CNCF のイベントでキャッチアップ
    - Knative / Rio by Rancher
    - CoreOS by OpenShift
    - kubeflow

## Nginx
- Nginx Plus
    - オールインワン
    - Microservices にも使える
- Nginx Unit
- Nginx Controller
- Nginx WAF
- etc...

## Docker セキュリティ
- プライベートリポジトリを用いるビルド
    - BuildKit 有効化 `export DOCKER=BUILDKIT=1`
    - `docker build --secret` および `docker build --ssh`
    - 詳しくは htts://github.com/moby/buildkit
        - なるべく早く Docker 18.09 に移行すべき
- イメージスキャナ
    - Microscanner / Clair etc...
    - どれが優れているとは一概には言えない
    - 依存パッケージを減らしてシンプルなイメージを作ることが重要
    - Seccomp / Apparmor / SELinux
- Docker ソケットを保護
    - TLS を適切に設定するのは難しいので SSH で保護する
- ランタイム
    - 基本的には Namespaces, Capabilities, Cgroups でできている
    - バインドマウントには注意が必要
    - コンテナ内の実行ユーザを指定する
        - dockerd --userns-remap というオプションがある
        - Rootless モードがこれから使えるようになる
- Docker / k8s 自体にも脆弱性は出てくる


## Dockerfile のベストプラクティス
- docs.docker.com で公開されている
- 1つずつ解説していた
    - ADD と RUN,COPY ではキャッシュの条件が異なる
    
## GitOps で始める Kubernetes CI/CD Pipeline
- manifest ファイルの git 管理
- CIOps は問題点も提唱されている
    - 複雑なパイプラインやクレデンシャルなど
    - CI がパイプラインの最後に k8s にデプロイするのはアンチパターンかも？
- 機密情報（secret）の扱い
- リソースの削除
    - git で消しても残る可能性がある
- GitOps を謳うツール
    - argo / weave flux / Jenkins X
- 感想：Spinnaker と GitOps の比較になる？


## showKs の舞台裏
- k8s の CI/CD をユーザー参加型で体験してもらう
- どんどん構成が複雑化
- PWA/SSR/BFF by Nuxt.js/Node.js etc...
- CI/CD/GitOps by Concourse/Spinnaker etc...
- クラウドネイティブで、Microservices 開発プロジェクトのオーナー体験をしてもらう
- 感想
    - これ追っかけるだけでだいぶ知識つく
    - 使われている技術スタックすごすぎる
    
## Kubernetes Meetup Tokyo 2年間の振り返り




