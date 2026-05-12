# 9router Docker

Docker setup for running `9router` installed via npm.

## Build and run with Docker

```bash
docker build -t 9router .
docker run --rm -p 3000:3000 9router
```

## Run with Docker Compose

```bash
docker compose up --build
```

This compose setup includes a named volume for persistent data:

- `9router_data` mounted at `/app/data`

## Test

In another terminal:

```bash
curl -i http://localhost:3000
```

## Custom port

```bash
docker run --rm -e PORT=8080 -p 8080:8080 9router
```

With Compose, update both `PORT` and `ports` in `docker-compose.yml`.

## Volume management

Inspect volume:

```bash
docker volume inspect 9r-docker_9router_data
```

Remove stack **and** volume:

```bash
docker compose down -v
```

## Healthcheck

The image includes a Docker healthcheck that requests:

```text
http://127.0.0.1:${PORT}/
```

Check health status with:

```bash
docker ps
```
