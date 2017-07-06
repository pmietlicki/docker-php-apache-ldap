docker-moodle
=============
[![](https://images.microbadger.com/badges/image/jhardison/moodle.svg)](https://microbadger.com/images/jhardison/moodle "Get your own image badge on microbadger.com")

A Dockerfile that installs and runs the latest Moodle 3.2 stable, with external MySQL Database.

Tags:
* latest - 3.2 stable
* v3.1 - 3.1 stable

## Installation

```
git clone https://github.com/jmhardison/docker-moodle
cd docker-moodle
docker build -t moodle .
```

## Usage

To spawn a new instance of Moodle:

```
docker run -d --name DB -p 3306:3306 -e MYSQL_DATABASE=moodle -e MYSQL_ROOT_PASSWORD=moodle -e MYSQL_USER=moodle -e MYSQL_PASSWORD=moodle mysql
docker run -d -P --name moodle --link DB:DB -e MOODLE_URL=http://192.168.59.103:8080 -p 8080:80 jhardison/moodle
```

You can visit the following URL in a browser to get started:

```
http://192.168.59.103:8080 
```

## Caveats
The following aren't handled, considered, or need work: 
* moodle cronjob (should be called from cron container)
* log handling (stdout?)
* email (does it even send?)

## Credits

This is a fork of [Jon Auer's](https://github.com/jda/docker-moodle) Dockerfile.
This is a reductionist take on [sergiogomez](https://github.com/sergiogomez/)'s docker-moodle Dockerfile.

