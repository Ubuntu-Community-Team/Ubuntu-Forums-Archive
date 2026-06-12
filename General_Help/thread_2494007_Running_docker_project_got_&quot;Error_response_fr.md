---
title: "Running docker project got &quot;Error response from daemon: readlink ...&quot; error"
date: 2024-01-02
forum: General Help
---

### Post by nilovsergey on 2024-01-02
Under kubuntu 22 I try to run old docker project, but I got error :


    ```
master@master-at-home:/_wwwroot/lar/BiCurrencies/__DOCKER$ docker compose up -d --build
    Error response from daemon: readlink /var/lib/docker/overlay2/l/NZKFX3UQ2GCYOP22Q6SO2TJX7A: no such file or directory
```


What I have now in my OS :

```

    $  lsb_release -d; uname -r; uname -i
    Description:    Ubuntu 22.04.3 LTS
    6.2.0-35-generic
    x86_64
    master@master-at-home:/_wwwroot/lar/BiCurrencies/__DOCKER$ dpkg -s   docker
    dpkg-query: package 'docker' is not installed and no information is available
    Use dpkg --info (= dpkg-deb --info) to examine archive files.
    master@master-at-home:/_wwwroot/lar/BiCurrencies/__DOCKER$ dpkg -s  docker-compose-plugin
    Package: docker-compose-plugin
    Status: install ok installed
    Priority: optional
    Section: admin
    Installed-Size: 59356
    Maintainer: Docker <support@docker.com>
    Architecture: amd64
    Source: docker-ce (5:24.0.6-1~ubuntu.22.04~jammy)
    Version: 2.21.0-1~ubuntu.22.04~jammy
    Enhances: docker-ce-cli
    Description: Docker Compose (V2) plugin for the Docker CLI.
     .
     This plugin provides the 'docker compose' subcommand.
     .
     The binary can also be run standalone as a direct replacement for
     Docker Compose V1 ('docker-compose').
    Homepage: [https://github.com/docker/compose](https://github.com/docker/compose)
    master@master-at-home:/_wwwroot/lar/BiCurrencies/__DOCKER$ dpkg -s  docker-buildx-plugin
    Package: docker-buildx-plugin
    Status: install ok installed
    Priority: optional
    Section: admin
    Installed-Size: 76085
    Maintainer: Docker <support@docker.com>
    Architecture: amd64
    Source: docker-ce (5:24.0.5-1~ubuntu.22.04~jammy)
    Version: 0.11.2-1~ubuntu.22.04~jammy
    Replaces: docker-ce-cli
    Enhances: docker-ce-cli
    Description: Docker Buildx cli plugin.
    Homepage: [https://github.com/docker/buildx](https://github.com/docker/buildx)

```

How to fix error and to run the project ?

---

### Post by nilovsergey on 2024-01-03
To clear dockers content I tried to run commands :

> docker compose down
docker stop $(docker ps -a -q)

docker rm $(docker ps -a -q)
docker compose down --remove-orphans
docker system prune --force --volumes



after that comman
> docker ps -a 

shows empty output

But when I try to run my docker projec I still got 
> master@master-at-home:/_wwwroot/lar/BiCurrencies/__DOCKER$ docker compose up -d --build
    Error response from daemon: readlink /var/lib/docker/overlay2/l/NZKFX3UQ2GCYOP22Q6SO2TJX7A: no such file or directory
    
error..

---

