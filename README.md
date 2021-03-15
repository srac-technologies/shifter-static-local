# Shifter (Static) - Local

Docker image for testing WordPress themes and plugins while migrating to Shifter. This image is also available on [Dockerhub](https://hub.docker.com/r/getshifter/shifter_local/).

## Requirements

- docker
- docker-compose

## Getting Started
cloneして以下のコマンドを実行

```
cd shifter-static-local
docker-compose build
docker-compose up -d
```

Visit [https://127.0.0.1:8443](https://127.0.0.1:8443) in your browser.

## docker-composした後
- PluginをActivate
  - Advanced Custom Fields
    - 記事属性を追加するのに必要
  - Code Snippets
    - カスタムブロックを追加するために必要
  - WP GraphQL
    - WordpressでGraphQLを有効にするために必要
  - WP GraphQL Gutenberg
    - Post.blocksを有効にするもの
  - WPGraphQL for Advanced Custom Fields
- Enable Public Introspectionをチェック


### Upgrade mysql 5.6 to 5.7

The included mysql version has been changed from 5.6 to 5.7.
If you want to keep the data, you can upgrade after starting docker-compose with the following command.

```
$ make mysql_upgrade
```

## Debugging

Some plugins and themes may conflict with Shifter. Conflicts usually cause the Generator to hang or fail. Here are a few tips.

### Check for a valid JSON format

Your site should return a list of valid URLs in JSON format for Shifter to crawl for generating.

Add `?url=0` to the websites URL to test.

[https://127.0.0.1:8443?urls=0](`https://127.0.0.1:8443?urls=0`)

his Docker image is similar to the one used by Shifter, but does not guarantee complete compatibility.

