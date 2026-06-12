---
title: "ubuntu 24.10 dist upgrade: docker lost images / changed config"
date: 2024-11-27
forum: General Help
---

### Post by Reimer_Prochnow on 2024-11-27
Hi all,
after a dist-upgrade from 24.04 to 24.10 docker is not working properly.
daemon starts (by sysctl as root) and even brings back persistent containers which were created with compose. These containers are still running (ps -ef) but unvisible to docker (docker ps).
docker images also shows not a single image.
While investigating, i found out that
- docker root dir changed to ~/.local/share/...
- docker switched to rootless mode, IMO also storage driver was switched

before upgrade I used rootful mode, and I think old containers / filesystems are still available in /var/lib/docker,
I tried to revert config in /etc/docker/damon.json -- this file seems pretty much as before, so configuration mode seems to have switch by default) but this file seems completely ignored.

---

### Post by Reimer_Prochnow on 2024-12-03
found issue by looking more deeply in "docker info" -- server version was different to client. Had a podman installation in parallel anf somehow this got default after dist-upgrade. Simply removed it and docker working again

---

