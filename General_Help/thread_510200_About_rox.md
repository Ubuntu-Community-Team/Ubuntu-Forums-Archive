---
title: "About rox"
date: 2007-07-26
forum: General Help
---

### Post by satimis on 2007-07-26
Hi folks,

Ubuntu 7.04 server amd64

Please advise which repo provides "rox", the light weight file manager?

$ sudo apt-cache search rox
can't find it.

TIA


B.R.
satimis

---

### Post by ThrobbingBrain66 on 2007-07-26
It's in the Universe repo: rox-filer

System>Administration>Software Sources

then tick the Universe checkbox and reload your sources.list file.

---

### Post by satimis on 2007-07-26
> **ThrobbingBrain66 said:**
> It's in the Universe repo: rox-filer

System>Administration>Software Sources

then tick the Universe checkbox and reload your sources.list file.
Hi ThrobbingBrain,

Sorry I'm running a light weight desktop - Fluxbox


$ cat /etc/apt/sources.list | grep universe```

## universe WILL NOT receive any review or updates from the Ubuntu security
deb http://hk.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ feisty universe
# deb http://hk.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://hk.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

```

universe is already there.

# sudo apt-get install rox-filer
it went throught w/o complaint.

$ which rox
/usr/bin/rox


I got it installed.  Tks


B.R.
satimis

---

