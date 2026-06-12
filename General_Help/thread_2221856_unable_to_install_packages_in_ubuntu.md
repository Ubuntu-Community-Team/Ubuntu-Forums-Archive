---
title: "unable to install packages in ubuntu"
date: 2014-05-04
forum: General Help
---

### Post by IAMTubby on 2014-05-04
Hello,
 I think I did something wrong with ppa's and now I'm not able to install any packages or even do a apt-get update.
To resolve I did the following
1. **sudo rm /etc/apt/sources.list**
2. **Ran software-properties-gtk and ticked the first 4 options in 'Downloadable from the Internet' which are main, universe, restricted and multiverse. The server is set to Main Server**
However, I'm still not able to perform an update or install any package. 

Please find attached the following files, after performing the above steps
1. guake.txt - output of running sudo apt-get install guake
2. apt-get-update.txt - output of running sudo apt-get update
3. sources-list.txt - my /etc/apt/sources.list

Please advise.
Thanks.

---

### Post by ofnuts on 2014-05-04
Not sure "Programming" is the best place to ask this...

Your sources.list looks rather different from mine and I don't think it's all due to my mor recent release:
```

# deb cdrom:[Kubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.1)]/ quantal main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ quantal universe
deb http://fr.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://fr.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security universe
deb-src http://security.ubuntu.com/ubuntu quantal-security universe
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main

```

So I would try to get hold of the original sources.list for your distro..

---

### Post by IAMTubby on 2014-05-04
> **ofnuts said:**
> 

Your sources.list looks rather different from mine and I don't think it's all due to my mor recent release:

thanks ofnuts, I copied and pasted your file from the previous post and I'm now able to download packages.
However, at the end of downloading packages, it says this for every package. How do I get rid of it ?
```

Download done.
Removing outdated cached downloads...
sha256sum mismatch jdk-6u45-linux-i586.bin
Oracle JDK 6 is NOT installed.
dpkg: error processing oracle-java6-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up guake (0.4.3-3) ...
Errors were encountered while processing:
 oracle-java6-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
IAMTubby@IAMTubby-Inspiron-1545:~$ 

```
I also did a sudo apt-get install oracle-java6-installer, but it too said the same as above, that oracle-java6-installer is not installed.

> 
Not sure "Programming" is the best place to ask this...

I'm sorry, didn't think and won't repeat for such system related issues.
But now that I have already posted, is it possible to change to a different forum ?

---

### Post by steeldriver on 2014-05-04
Moved to the 'General Help' forum
 
The Oneiric Ocelot release reached end of life almost a year ago - the repositories have been taken offline, I think

```

deb http://archive.ubuntu.com/ubuntu **oneiric** main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ **oneiric-security** universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu **oneiric-updates** universe main multiverse restricted

```

See

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by IAMTubby on 2014-05-04
Thanks ofnuts, steeldriver.
Marking the thread as solved.

---

