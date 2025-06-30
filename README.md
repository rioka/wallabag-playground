# Wallabag Playground

- Download docker image

  ```
  docker pull wallabag/wallabag
  ```

## Run with SQLite

Running Wallabag with SQLite is the simplest setup:

```
$ docker run -p 80:80 -e "SYMFONY__ENV__DOMAIN_NAME=http://localhost" wallabag/wallabag
```

> Default login is `wallabag`/`wallabag`

## Run with PostgreSQL

```
$ docker run --name wallabag-db -e "POSTGRES_PASSWORD=my-secret-pw" -e "POSTGRES_USER=my-super-user" -d postgres:9.6
$ docker run --name wallabag --link wallabag-db:wallabag-db -e "POSTGRES_PASSWORD=my-secret-pw" -e "POSTGRES_USER=my-super-user" -e "SYMFONY__ENV__DATABASE_DRIVER=pdo_pgsql" -e "SYMFONY__ENV__DATABASE_HOST=wallabag-db" -e "SYMFONY__ENV__DATABASE_PORT=5432" -e "SYMFONY__ENV__DATABASE_NAME=wallabag" -e "SYMFONY__ENV__DATABASE_USER=wallabag" -e "SYMFONY__ENV__DATABASE_PASSWORD=wallapass" -e "SYMFONY__ENV__DOMAIN_NAME=http://localhost" -p 80:80 wallabag/wallabag
```

## Run with Docker compose

See [this template](https://github.com/wallabag/wallabag/blob/master/compose.yaml)

## References

- [What is wallabag?](https://hub.docker.com/r/wallabag/wallabag/)
- [Installation](https://doc.wallabag.org/admin/installation/)
- [Source code](https://github.com/wallabag/wallabag/)