---
title: "help with apt-cacher/synaptic"
date: 2005-10-07
forum: General Help
---

### Post by dieselpower on 2005-10-07
I am having a terrible time with apt-cacher/synaptic, It worked so well with debian and now i'm just about to leave my computer for a month! It cannot download about half the repositories, and I do not know if it is my problem or if I am using the wrong repositories. here is my /etc/apt/sources.list.

```

## Uncomment the following two lines to fetch updated software from the network
deb http://server/apt-cacher/us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://server/apt-cacher/us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://server/apt-cacher/us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://server/apt-cacher/us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://server/apt-cacher/us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://server/apt-cacher/us.archive.ubuntu.com/ubuntu hoary universe

deb http://server/apt-cacher/security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://server/apt-cacher/security.ubuntu.com/ubuntu hoary-security main restricted

deb http://server/apt-cacher/security.ubuntu.com/ubuntu hoary-security universe
deb-src http://server/apt-cacher/security.ubuntu.com/ubuntu hoary-security universe

deb http://server/apt-cacher/archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://server/apt-cacher/archive.ubuntu.com/ubuntu hoary multiverse

## Backports

deb http://server/apt-cacher/acm.cs.umn.edu/ubp/ hoary-backports main universe multiverse restricted
deb http://server/apt-cacher/acm.cs.umn.edu/ubp/ hoary-extras main universe multiverse restricted

## Demudi
deb http://server/apt-cacher/demudi.agnula.org/packages/demudi testing main

## KDE
deb http://server/apt-cacher/kubuntu.org/hoary-kde342 hoary-updates main

deb http://server/apt-cacher/kubuntu.org/kde35beta1 hoary main
deb ftp://bolugftp.uni-bonn.de/pub/kde/unstable/3.5-beta1/kubuntu hoary main
deb http://server/apt-cacher/www.mirrorservice.org/sites/ftp.kde.org/pub/kde/unstable/3.5-beta1/kubuntu hoary main
deb http://server/apt-cacher/mirror.cc.columbia.edu/pub/software/kde/unstable/3.5-beta1/kubuntu hoary main

```

server is the machine that apt-cacher is running on, and some of them work. but about 35% do not. and it seems like more of them work on server than they do on this computer (lawrence)

I do not like apt-proxy. apt cacher is much easier for me to use and it will actually import packages.

does anybody have a working sources.list that includes Demudi and backports at least?

Thank you, Now maybe I won't smash it yet!

---

