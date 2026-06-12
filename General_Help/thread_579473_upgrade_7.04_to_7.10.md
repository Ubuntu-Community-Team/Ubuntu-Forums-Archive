---
title: "upgrade 7.04 to 7.10"
date: 2007-10-18
forum: General Help
---

### Post by ali780 on 2007-10-18
Hi
I tried to upgrade my ubuntu 7.04 to 7.10.
I faced with the following error:

> A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found
Failed to fetch [http://www.debian-multimedia.org/dists/sarge/main/binary-i386/Packages.gz](http://www.debian-multimedia.org/dists/sarge/main/binary-i386/Packages.gz) 404 Not Found


How can I fix it?
Thanks

---

### Post by peachy on 2007-10-18
can you paste your sources.list pls

# cat /etc/apt/sources.list

---

### Post by ali780 on 2007-10-18
This is the source:
> 
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## MAIN REPOSITORIES
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
# deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

## SEVEAS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) dapper-seveas all

# CIPHERFUNK REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

## WINE REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## OPERA REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## XGL/COMPIZ REPOSITORIES (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
# deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

## DEBIAN REPOSITORIES (Unsupported.  May contain illegal packages.  Use at own risk.)
## deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main
## deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main
## deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

## skype 
## only uncomment it if you need it
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
## Medibuntu - Ubuntu 6.10 “feisty”
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sarge main

---

### Post by ali780 on 2007-10-18
I should also mention that when I try to do upgrade first it say that I should do partial upgrade as follow:
Not all updates can be installed
this can be caused by 
1-a previous upgrade which did not complete
2-
3-...

---

### Post by Velociraptor on 2007-10-20
I also got the "Failed to fetch http://medibuntu.sos-sts.com/..." while upgrading to gutsy.

Managed to fix by going to the menu: Applications-> Add/Remove.., and clicking on the Preferences button, Third Party Software tab, and deselecting those repositories.

Note these repositories were already commented out in my /etc/apt/sources.list, so that wasn't the cause of the problem for me. But you should try commenting them out in your sources.list, just add a # character to the start of the line.

---

