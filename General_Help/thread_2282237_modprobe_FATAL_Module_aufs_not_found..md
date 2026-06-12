---
title: "modprobe: FATAL: Module aufs not found."
date: 2015-06-12
forum: General Help
---

### Post by ROVguy on 2015-06-12
I have been trying to insall Docker on my SP3 running Ubuntu 14.04.2.  From what I understand it seems that my kernel is having issues.  After running this comand
"**wget -qO- https:****//get.docker.com/ | sh**" I immediately  get this error "**modprobe: FATAL: Module aufs not found.**"
From this site "**[https://meta.discourse.org/t/docker-install-module-aufs-not-found/18494/6](https://meta.discourse.org/t/docker-install-module-aufs-not-found/18494/6)**" it appears that I need to install 
[B]"sudo apt-get install lxc wget bsdtar curl"
"sudo apt-get install linux-image-extra-$(uname -r)"
"sudo modprobe aufs"[/B]

But when I do the 2nd line I get two errors. 
"**E: Unable to locate package linux-image-extra-3.19.0-031900-generic**"
"**E: Couldn't find any package by regex 'linux-image-extra-3.19.0-031900-generic'**"

Any sugestions on what is the issue and how to get Docker installed and setup properly?

Thanks

---

