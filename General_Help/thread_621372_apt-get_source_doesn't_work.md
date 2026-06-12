---
title: "apt-get source doesn't work"
date: 2007-11-23
forum: General Help
---

### Post by thegnuguru on 2007-11-23
```
matt@matt-desktop:~/packages$ apt-get source wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_main_source_Sources - open (2 No such file or directory)

```

---

### Post by kaiju on 2007-11-24
did you check your /etc/apt/sources.list file for bad links?
```
gksudo gedit /etc/apt/sources.list
```

for fetching source packages, you should have an entry like this:
```
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
```

---

