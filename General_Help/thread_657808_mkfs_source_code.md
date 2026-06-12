---
title: "mkfs source code"
date: 2008-01-04
forum: General Help
---

### Post by Sebrent on 2008-01-04
I've been trying my hardest to find the source code for **mkfs** but apparently I'm too retarded to find it#-o

Could anyone please point me in the right direction to find it?  I had been told to look in e2fsprogs, but I can't seem to find the source code in it.

---

### Post by geirha on 2008-01-04
General procedure to get the source code of a package:

Find out which package it's in:
```

$ which mkfs
/sbin/mkfs
$ dpkg -S /sbin/mkfs
util-linux: /sbin/mkfs

```

get the source code for that package:
```
$ cd /tmp
$ apt-get source util-linux

```
You should now have a directory called util-linux-something which contains the source code (disk-utils/mkfs.c sounds like the one)

---

### Post by Sebrent on 2008-01-04
Thank you very much, geirha, that worked splendidly .

For anyone else looking for mkfs.c, it is in the **disk-utils** folder of the package.

---

### Post by myle on 2008-01-15
I want to download the source code of ls and I have the following problem. What's wrong?

> myle@myle-desktop:~/Desktop/source$ sudo apt-get source coreutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_main_source_Sources - open (2 No such file or directory)


My source.list is:
```
#I have added the following line when I was trying to fix the problem
#deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gr.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ gutsy restricted main universe
#Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://gr.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gr.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gr.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gr.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse #Added by software-properties

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://ftp.duth.gr/pub/ubuntu/ gutsy main universe restricted multiverse
deb-src http://ftp.duth.gr/pub/ubuntu/ gutsy main universe restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted #Added by software-properties#I have added the following line when I was trying to fix the problem
#deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gr.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ gutsy restricted main universe
#Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://gr.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gr.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gr.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gr.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse #Added by software-properties

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://ftp.duth.gr/pub/ubuntu/ gutsy main universe restricted multiverse
deb-src http://ftp.duth.gr/pub/ubuntu/ gutsy main universe restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted #Added by software-properties
deb http://ftp.duth.gr/pub/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://ftp.duth.gr/pub/ubuntu/ gutsy-updates universe main multiverse restricted #Added by software-properties

deb http://packages.medibuntu.org/ gutsy free non-free

## Seveas
deb http://mirror.ubuntulinux.nl gutsy-seveas all
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted #Added by software-properties
deb-src http://mirror.ubuntulinux.nl gutsy-seveas all
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ gutsy main
deb http://gauvain.tuxfamily.org/repos gutsy contrib
deb-src http://gauvain.tuxfamily.org/repos gutsy contrib
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse #Added by software-properties
deb http://ubuntu.beryl-project.org edgy main
deb [http://ftp.duth.gr/pub/ubuntu/](http://ftp.duth.gr/pub/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://ftp.duth.gr/pub/ubuntu/](http://ftp.duth.gr/pub/ubuntu/) gutsy-updates universe main multiverse restricted #Added by software-properties

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

## Seveas
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) gutsy-seveas all
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted #Added by software-properties
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) gutsy-seveas all
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) gutsy main
deb [http://gauvain.tuxfamily.org/repos](http://gauvain.tuxfamily.org/repos) gutsy contrib
deb-src [http://gauvain.tuxfamily.org/repos](http://gauvain.tuxfamily.org/repos) gutsy contrib
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse #Added by software-properties
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
```

---

