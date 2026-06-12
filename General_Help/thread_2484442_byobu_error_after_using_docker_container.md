---
title: "byobu error after using docker container"
date: 2023-02-26
forum: General Help
---

### Post by tejesw4r on 2023-02-26
getting this errors after using docker containers


Ubuntu-server kernel: [42329.158744] tmux: server[5282]: segfault at 80 ip 0000000000000080 sp 00007ffdc06c4c68 error 14 in tmux[555c2d941000+19000]
Ubuntu-server kernel: [42329.158769] Code: Unable to access opcode bytes at RIP 0x56.



it stopping all running programs in byobu

---

### Post by MAFoElffen on 2023-02-27
There is no context to this to even guess at what may  be going on. The title says you get this error after using a docker container... The error, content of your post, and error messages say tmux...

First, please run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") so we know what you have and a bit on how it is configured. Please post the URL of what pastebin the report gets uploaded to.

Then:
```

docker --version

```
Then tell us what the Docker container was, with what application and if it ran completion(?)

The tell us what you were running in tmux terminal
```

tmux -V
ps  -e | grep tmux

```

---

### Post by tejesw4r on 2023-02-27
here system info: [https://paste.ubuntu.com/p/7XdjGbJJZn/](https://paste.ubuntu.com/p/7XdjGbJJZn/)

docker version: 20.10.12, build 20.10.12-0ubuntu4

byobu version 5.133
tmux 3.2a


ps  -e | grep tmux
   1792 ?        00:06:39 tmux: server

I am running windows programs with the help of wine in the byobu session in both the docker container and ubuntu.
after started using the docker container everything seems fine. but some days later the "server exited unexpectedly" has coming and it stops all running programs in the byobu session. it does not affect or stop programs in docker containers

---

