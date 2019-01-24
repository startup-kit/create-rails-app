# create-rails-app

## Execute commands in services

The general structure of the `exec` command is:

```bash
$ docker-compose exec <service> <command>
```

`<service>` is the name of the container service as described in the `docker-compose.yml` file and `<command>` is the command you want to launch inside the service.

## Run with other services

### Sidekiq

```yaml
services:
  ...
  redis:
    image: redis

  worker:
    build: .
    command: bundle exec sidekiq -C config/sidekiq.yml -e development
    depends_on:
      - redis
```

## References

- [Best practices for writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)

## License

Create Rails App © Sam Yamashita. Released under the [MIT](LICENSE)<br/>
Authored and maintained by Sam Yamashita with help from [contributors](https://github.com/sotayamashita/create-rails-app/contributors).
