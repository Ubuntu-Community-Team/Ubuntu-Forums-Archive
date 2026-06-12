---
title: "Ubuntu upgrade"
date: 2007-06-11
forum: General Help
---

### Post by madsurfer on 2007-06-11
Hi

I decided to upgrade my 6.10 Ubuntu to 7.04, however it was going to take 14 hours to download and do. I searched on google and found the following link
[http://ubuntu.wordpress.com/2005/10/...aster-upgrade/](http://ubuntu.wordpress.com/2005/10/...aster-upgrade/)

This seemed like a good way to change my sources.list to a local mirror. However I do not know what in the souces.list to change. Currently my list is as shown:-s

deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Added by Adrian
# deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) dapper-seveas all
# deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) dapper-seveas all

# Added by Adrian
# deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx

# Added by Adrian
# deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) sarge main

# Added by Adrian
# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
# deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free

# deb [http://packages.freecontrib.org/ubuntu/freecontrib/](http://packages.freecontrib.org/ubuntu/freecontrib/) edgy free non-free
# deb-src [http://packages.freecontrib.org/ubuntu/freecontrib/](http://packages.freecontrib.org/ubuntu/freecontrib/) edgy free non-free

# Added by Adrian
# deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all
# deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all


and I was going to use the following mirror :
[http://ubuntu.virginmedia.com/releases/](http://ubuntu.virginmedia.com/releases/)

I know it is a basic question but what do I change? Also what about the security repositories, does the mirror have these?

Adrian

---

### Post by zvacet on 2007-06-11
Try this source list

[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

In system>administration<software sources you can choose local mirror

---

### Post by madsurfer on 2007-06-11
Thanks for the information, this link only shows how to use the standard package.list, how do I change to a mirror? Also what happens to the security repositories? Also using the software sources option from the administration menu only gives me the main server or usa server not a local mirror. Can this be changed?

---

### Post by zvacet on 2007-06-11
It is option called** other**.Second option is on the page from link I give to you.You probably ovelooked it.

> To use your local mirror you can add "cc." before archive.ubuntu.com, where cc = your country code

---

