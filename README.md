# Docker For PHP Developers

[![Build Status](https://img.shields.io/travis/php-earth/docker-php/master.svg?style=plastic)](https://travis-ci.org/php-earth/docker-php) [![Docker Automated build](https://img.shields.io/docker/automated/phpearth/php.svg?style=plastic)](https://hub.docker.com/r/phpearth/php/) [![MIT License](https://img.shields.io/github/license/php-earth/docker-php.svg?style=plastic "MIT License")](https://github.com/php-earth/docker-php/blob/master/LICENSE)

Carefully crafted Docker images for PHP developers with latest PHP versions 7.1 and upcoming 7.2, [Nginx](https://nginx.org/), [OpenLiteSpeed](http://open.litespeedtech.com/) and [Apache HTTP Server](https://httpd.apache.org/).

* Fast and simple PHP extensions installation
* Optional [Composer](https://getcomposer.org) installation
* [runit](http://smarden.org/runit/) for running multiple services without overhead.
* Alpine base image with PHP.earth Alpine PHP repositories
* Optimized Docker image sizes

## Docker Tags

The following list contains all current Docker tags and what is included in each.

| System | Docker Tag | Features | Size |
| ------ | ---------- | -------- | ---- |
| **PHP 7.1.6**@Alpine 3.6 | [`latest`, `7.1`](https://github.com/php-earth/docker-php/tree/master/docker/Dockerfile-7.1) | PHP CLI | [![](https://images.microbadger.com/badges/image/phpearth/php.svg)](https://microbadger.com/images/phpearth/php "Image size") |
| | [`7.1-litespeed`](https://github.com/php-earth/docker-php/tree/master/docker/Dockerfile-7.1-litespeed) | OpenLiteSpeed 1.4.26 | [![](https://images.microbadger.com/badges/image/phpearth/php:7.1-litespeed.svg)](https://microbadger.com/images/phpearth/php:7.1-litespeed "Image size") |
| | [`7.1-nginx`](https://github.com/php-earth/docker-php/tree/master/docker/Dockerfile-7.1-nginx) | Nginx 1.12.0, FPM | [![](https://images.microbadger.com/badges/image/phpearth/php:7.1-nginx.svg)](https://microbadger.com/images/phpearth/php:7.1-nginx "Image size") |
| | [`7.1-apache`](https://github.com/php-earth/docker-php/tree/master/docker/Dockerfile-7.1-apache) | Apache 2.4.25 | [![](https://images.microbadger.com/badges/image/phpearth/php:7.1-apache.svg)](https://microbadger.com/images/phpearth/php:7.1-apache "Image size") |
| | [`7.1-cgi`](https://github.com/php-earth/docker-php/tree/master/docker/Dockerfile-7.1-cgi) | PHP CGI | [![](https://images.microbadger.com/badges/image/phpearth/php:7.1-cgi.svg)](https://microbadger.com/images/phpearth/php:7.1-cgi "Image size") |
| **PHP 7.2.0alpha2**@Alpine 3.6 | [`7.2`](https://github.com/php-earth/docker-php/tree/master/docker/Dockerfile-7.2) | PHP CLI | [![](https://images.microbadger.com/badges/image/phpearth/php:7.2.svg)](https://microbadger.com/images/phpearth/php:7.2 "Image size") |
| | [`7.2-litespeed`](https://github.com/php-earth/docker-php/tree/master/docker/Dockerfile-7.2-litespeed) | OpenLiteSpeed 1.4.26 | [![](https://images.microbadger.com/badges/image/phpearth/php:7.2-litespeed.svg)](https://microbadger.com/images/phpearth/php:7.2-litespeed "Image size") |
| | [`7.2-nginx`](https://github.com/php-earth/docker-php/tree/master/docker/Dockerfile-7.2-nginx) | Nginx 1.12.0, FPM | [![](https://images.microbadger.com/badges/image/phpearth/php:7.2-nginx.svg)](https://microbadger.com/images/phpearth/php:7.2-nginx "Image size") |
| | [`7.2-apache`](https://github.com/php-earth/docker-php/tree/master/docker/Dockerfile-7.2-apache) | Apache 2.4.25 | [![](https://images.microbadger.com/badges/image/phpearth/php:7.2-apache.svg)](https://microbadger.com/images/phpearth/php:7.2-apache "Image size") |
| | [`7.2-cgi`](https://github.com/php-earth/docker-php/tree/master/docker/Dockerfile-7.2-cgi) | PHP CGI | [![](https://images.microbadger.com/badges/image/phpearth/php:7.2-cgi.svg)](https://microbadger.com/images/phpearth/php:7.2-cgi "Image size") |

Tags follow PHP release cycle and [PHP supported versions timeline](http://php.net/supported-versions.php).

| PHP | Active Support Until | Security Support Until |
| --- | -------------------- | ---------------------- |
| 7.1 | 2018-12-01           | 2019-12-01             |
| 7.2 | TBD                  | TBD                    |

## Quick Usage

### Nginx

For example, to run an Nginx HTTP server with PHP FPM, create a `Dockerfile`:

```Dockerfile
FROM phpearth/php:7.1-nginx
```

And then build Docker image and run Docker container:

```bash
docker build -t custom-php .
docker run --name custom-php-container -p 80:80 -d custom-php
```

### PHP CLI

To run a CLI PHP script:

```bash
docker run -it --rm -v `pwd`:/usr/src/myapp -w /usr/src/myapp phpearth/php php script.php
```

### Composer

To install Composer:

```Dockerfile
FROM phpearth/php:7.1-nginx

RUN apk add --no-cache composer
```

### PHP Extensions

PHP extensions installation:

```Dockerfile
FROM phpearth/php:7.1-litespeed

RUN apk add --no-cache php71-libsodium php71-intl php71-pdo_mysql
```

## Documentation

A more detailed documentation and cookbook with Docker and PHP recipes:

* [Intro](https://github.com/php-earth/docker-php/blob/master/docs/01-intro.md)
* [Usage](https://github.com/php-earth/docker-php/blob/master/docs/02-usage.md)
* [Composer](https://github.com/php-earth/docker-php/blob/master/docs/03-composer.md)
* [Building PHP From Source](https://github.com/php-earth/docker-php/blob/master/docs/04-php.md)
* [PHP Extensions](https://github.com/php-earth/docker-php/blob/master/docs/05-php-extensions.md)
* [Permissions](https://github.com/php-earth/docker-php/blob/master/docs/06-permissions.md)
* [Certbot](https://github.com/php-earth/docker-php/blob/master/docs/07-certbot.md)
* [Building Images](https://github.com/php-earth/docker-php/blob/master/docs/08-build.md)
* [Alpine Linux](https://github.com/php-earth/docker-php/blob/master/docs/09-alpine.md)
* [Recipes](https://github.com/php-earth/docker-php/blob/master/docs/10-recipes.md)

## License and Contributing

[Contributions](https://github.com/php-earth/docker-php/blob/master/CONTRIBUTING.md) are most welcome. This repository is released under the [MIT license](https://github.com/php-earth/docker-php/blob/master/LICENSE).
