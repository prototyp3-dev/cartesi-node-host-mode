
# Cartesi Node Host Mode

```
Cartesi Rollups version: 0.9.x
```

This project is a simple way to run Cartesi node on host mode using a local chain to test your code without the need to build the Cartesi Machine. Simply dowload the docker compose file, start docker compose, and start the Backend DApp code on the host machine

## Requirements

Docker version `20.10.14` with [Docker Buildkit](https://github.com/moby/buildkit) enabled.

## Run host mode

To start the Cartesi node on host mode using a local chain run:

```shell
curl https://github.com/prototyp3-dev/cartesi-node-host-mode/blob/main/docker-compose.yml -o docker-compose.yml
docker compose up -d
```

Stop running the node with

```shell
docker compose down -v
```

## Create and Test new project with Sunodo CLI

Using [sunodo cli](https://github.com/sunodo/sunodo/blob/main/apps/cli/README.md) you can create a project and test using host mode. 

As an example, we will create a python dapp and run on host mode. To create the dapp you can run

```shell
sunodo create my-dapp --template=python
```

While the cartesi node in host mode is running, you can run your backend code with:

```shell
cd my-dapp
python3 -m venv .venv
. .venv/bin/activate
pip install -r requirements.txt
ROLLUP_HTTP_SERVER_URL="http://127.0.0.1:5004" python3 dapp.py
```
