# 変更点

Ubuntu Server 24.04 LTSで試した際に、動かなかったので以下の修正を加えている

* `docker-compose`から`docker compose`に変更
  * 理由は24.04で`docker-compose`が動かないから

* `mysqld.sock`から`mysql.sock`に変更
  * 理由はソケット名が変わっているから

## 残タスク

これで最低限動くようになったが、まだ修正する箇所はある。

* `docker-compose.yml`のVersion記述を削除
  * 理由は`docker compose`になってからversion記述が不要になったため

* `wp_config.php`の`DB_HOST`に`mysql.sock`のパスを追加する
  * 理由はデフォルトのままだと通信できない。

```php
define( 'DB_HOST', 'localhost:/var/lib/mysql/mysql.sock' )
```

[参考](https://easyramble.com/wordpress_mysql_socket_error.html)

* `sudo`を追加したが、dockerグループに所属しているなどで`sudo`がいらない場合の処理を追加する

* オプション指定で`Cloudflare Tunnel`も使えるようにする

---

## KUSANAGI Runs on Docker

KUSANAGI Runs on Docker (hereinafter RoD) provides the functions of KUSANAGI using Docker compose.

## How to Install

For install kusanagi RoD, run this commands localy. And install kusanagi-docker command and other files in ```$HOME/.kusanagi```.

```bash
curl https://raw.githubusercontent.com/prime-strategy/kusanagi-docker/master/install.sh | bash
```

## How to Run

For use KUSANAGI RoD, run kusanagi-docker command. Recommended to add "$HOME /.kusanagi/bin" in the environment variable PATH.
And simple help is run kusanagi-docker help.

## Recommends or Requires

### Recommends OS

* CentOS7 or later
* Ubuntu18.04 or later
* Windows10/Windows11(WSL2 + DockerCE)
* Windows10/Windows11(WSL2 + Docker Desktop for Windows)
* Mac(with Docker Desktop for mac)

### Requre commands

* bash(over 4.x)
* git
* sed
* awk
* grep
* gettext(gettext.sh, envsubst)
* curl
* docker(over 18.0x)
* docker-compose
* docker-machine
