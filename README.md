# アプリケーション名(ログイン機能なし)

## 準備手順の前に確認すること(この手順はアプリ完成時には README から削除する)

-   Docker Desktop で全コンテナを停止させる  
    コンテナが複数起動するとポートがバッティング起こしてエラーするので全部止めてからやる

-   Docker Desktop で不要なリソースを定期的に削除する  
    ストレージを圧迫するので、Containers/Images/Volumes あたりは定期的に掃除する  
    docker compose up コマンドしたら全部再生成されるので分からなかったら全削除

-   Ubuntu または mac 内の勉強データで不要なものは定期的に削除する  
    git clone で色々作ってもらってるので作業ディレクトリにたくさんファイルやフォルダがあると思うので  
    不要だと判断できるアプリデータは削除する  
    `rm ファイル名`もしくは`rm -r ディレクトリ名`で削除する  
    ※間違えて大事なファイルを削除しないようにだけ気をつけてください...  
    ※怖かったらこれはやらなくて OK

-   このリポジトリは arm 版です(AppleSilicon の Mac 向け)  

## Git リポジトリの準備手順(この手順はアプリ完成時には README から削除する)

-   リモートリポジトリの作成  
    GitHub でリモートリポジトリを作成する(Add a README file のチェックは外す)  
    リポジトリ名は作るアプリケーションに合わせる  
    このリポジトリは下記説明で出てくる{上で作成したリモートリポジトリ}の事になる

-   カレントディレクトリを変更する  
    コマンドラインで現在いるディレクトリを作業ディレクトリに移動してから行う  
    ※こだわりが無ければ coachtech ディレクトリに移動してから下記コマンドを行う

-   2 つのリポジトリをクローンしてファイル移動する

```
git clone git@github.com:tamachima327/laravel-template-nologin-arm.git
```

```
yes | rm -r laravel-template-nologin-arm/.git
```

```
git clone 上で作成したリモートリポジトリのSSHアドレス(Codeからコピー)
```

```
mv laravel-template-nologin-arm/* laravel-template-nologin-arm/.[^\.]* 上で作成したリモートリポジトリ名
```

```
rm -r laravel-template-nologin-arm
```

```
cd 上で作成したリモートリポジトリ名
```

```
code .
```

## 環境構築手順

-   コンテナを立ち上げるため、以下を実行

```
docker compose up -d --build
```

-   env ファイルの作成をするため、以下を実行

```
cp src/.env.example src/.env
```

-   php にコンテナに入るため、以下を実行

```
docker compose exec php bash
```

-   composer パッケージをインストールするため、以下を実行

```
composer install
```

-   アプリケーションキーを作成するため、以下を実行

```
php artisan key:generate
```

-   マイグレーションを実行するため、以下を実行

```
php artisan migrate
```

## 環境構築手順が終わった後にやること(この手順はアプリ完成時には README から削除する)

-   ブラウザで動作チェック  
    localhost にアクセスして動作確認  
    localhost:8080 にアクセスして phpmyadmin が見れるか確認

-   環境構築手順で動くことを確認したら commit/push して環境構築完了  
    コミットメッセージは"First commit"

## 開発でやる必要があること(この手順はアプリ完成時には README から削除する)

-   view ファイルの作成・修正・削除
-   controller の作成・修正
-   model の作成・修正
-   css の作成・修正・削除(クラス名も直すこと)
-   migration ファイルの作成・修正
-   seeder の作成
-   README.md(このファイル)の修正
