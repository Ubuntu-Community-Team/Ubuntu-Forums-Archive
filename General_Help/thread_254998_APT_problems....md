---
title: "APT problems..."
date: 2006-09-10
forum: General Help
---

### Post by Demio on 2006-09-10
Hello everyone, 

Everything has been working perfectly untill today. I tried to get some new packages on synaptic and I got an error, then I tried it in the console and this is what I get: 

```
demio@DEMENTOR:~$ sudo apt-get update
Ign http://theli.free.fr dapper Release.gpg
Ign http://blognux.free.fr unstable Release.gpg
Get:1 http://ubuntu.compiz.net dapper Release.gpg [189B]
Get:2 http://xgl.compiz.info dapper Release.gpg [189B]
Get:3 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Ign http://exodus.xmms.se dapper Release.gpg
Get:4 http://security.ubuntu.com dapper-security Release.gpg [189B]
Hit http://theli.free.fr dapper Release
Ign http://packages.freecontrib.org dapper Release.gpg
Ign http://blognux.free.fr unstable Release
Hit http://archive.canonical.com dapper-commercial Release
Get:5 http://xgl.compiz.info dapper Release [5405B]
Ign http://exodus.xmms.se dapper Release
Ign http://packages.freecontrib.org dapper Release
Ign http://theli.free.fr dapper/listen Packages
Get:6 http://www.beerorkid.com dapper Release.gpg [189B]
Ign http://exodus.xmms.se dapper/main Packages
Ign http://packages.freecontrib.org dapper/free Packages
Ign http://download.skype.com stable Release.gpg
Ign http://blognux.free.fr unstable/main Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Ign http://xgl.compiz.info dapper/main Packages
Ign http://packages.freecontrib.org dapper/non-free Packages
Get:7 http://ubuntu.compiz.net dapper Release [5405B]
Hit http://exodus.xmms.se dapper/main Packages
Hit http://theli.free.fr dapper/listen Packages
Get:8 http://xgl.compiz.info dapper/main Packages [12.7kB]
Hit http://packages.freecontrib.org dapper/free Packages
Hit http://security.ubuntu.com dapper-security Release
Hit http://blognux.free.fr unstable/main Packages
Get:9 http://www.beerorkid.com dapper Release [5405B]
Ign http://download.skype.com stable Release
Ign http://ubuntu.compiz.net dapper/main Packages
Hit http://packages.freecontrib.org dapper/non-free Packages
Get:10 http://ubuntu.compiz.net dapper/main Packages [12.7kB]
Hit http://security.ubuntu.com dapper-security/main Packages
Ign http://download.skype.com stable/non-free Packages
Get:11 http://media.blutkind.org dapper Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://download.skype.com stable/non-free Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://media.blutkind.org dapper Release
Ign http://www.beerorkid.com dapper/main Packages
Ign http://media.blutkind.org dapper/main Packages
Hit http://media.blutkind.org dapper/main Packages
Ign http://www.beerorkid.com dapper/main Packages
Get:12 http://www.beerorkid.com dapper/main Packages [12.7kB]
Get:13 http://www.beerorkid.com dapper/main Packages [12.7kB]
99% [13 Packages gzip 0] [Waiting for headers] [Waiting for headers]
gzip: stdin: not in gzip format
Err http://www.beerorkid.com dapper/main Packages
  Sub-process gzip returned an error code (1)
Get:14 http://www.getautomatix.com dapper Release.gpg [189B]
Hit http://www.getautomatix.com dapper Release
Hit http://www.getautomatix.com dapper/main Packages
Ign http://pt.archive.ubuntu.com dapper Release.gpg
Ign http://pt.archive.ubuntu.com dapper-updates Release.gpg
Ign http://pt.archive.ubuntu.com dapper-backports Release.gpg
Ign http://pt.archive.ubuntu.com dapper Release
Ign http://pt.archive.ubuntu.com dapper-updates Release
Ign http://pt.archive.ubuntu.com dapper-backports Release
Ign http://pt.archive.ubuntu.com dapper/main Packages
Ign http://pt.archive.ubuntu.com dapper/restricted Packages
Ign http://pt.archive.ubuntu.com dapper/universe Packages
Ign http://pt.archive.ubuntu.com dapper/multiverse Packages
Ign http://pt.archive.ubuntu.com dapper/main Packages
Ign http://pt.archive.ubuntu.com dapper/restricted Packages
Ign http://pt.archive.ubuntu.com dapper/main Sources
Ign http://pt.archive.ubuntu.com dapper/restricted Sources
Ign http://pt.archive.ubuntu.com dapper/universe Packages
Ign http://pt.archive.ubuntu.com dapper/universe Sources
Ign http://pt.archive.ubuntu.com dapper-updates/main Sources
Ign http://pt.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://pt.archive.ubuntu.com dapper-backports/main Packages
Ign http://pt.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://pt.archive.ubuntu.com dapper-backports/universe Packages
Ign http://pt.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://pt.archive.ubuntu.com dapper-backports/main Sources
Ign http://pt.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://pt.archive.ubuntu.com dapper-backports/universe Sources
Ign http://pt.archive.ubuntu.com dapper-backports/multiverse Sources
Err http://pt.archive.ubuntu.com dapper/main Packages
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper/restricted Packages
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper/universe Packages
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper/multiverse Packages
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper/main Packages
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper/restricted Packages
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper/main Sources
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper/restricted Sources
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper/universe Packages
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper/universe Sources
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper-updates/main Sources
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper-updates/restricted Sources
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper-backports/main Packages
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper-backports/restricted Packages
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper-backports/universe Packages
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper-backports/multiverse Packages
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper-backports/main Sources
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper-backports/restricted Sources
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper-backports/universe Sources
  403 Forbidden
Err http://pt.archive.ubuntu.com dapper-backports/multiverse Sources
  403 Forbidden
Fetched 54.8kB in 1m33s (586B/s)
Failed to fetch http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz  403 Forbidden
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz  403 Forbidden
Reading package lists... Done
W: Duplicate sources.list entry http://pt.archive.ubuntu.com dapper/main Packages (/var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry http://pt.archive.ubuntu.com dapper/restricted Packages (/var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://pt.archive.ubuntu.com dapper/universe Packages (/var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://www.beerorkid.com dapper/main Packages (/var/lib/apt/lists/www.beerorkid.com_compiz_dists_dapper_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

This is my sources.list:
```

deb http://pt.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://packages.freecontrib.org/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb http://pt.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu/ dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://pt.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://pt.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://pt.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://pt.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://pt.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
## Repository for Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
deb http://blognux.free.fr/debian unstable main
deb http://www.getautomatix.com/apt dapper main
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb http://www.beerorkid.com/compiz dapper main
deb http://media.blutkind.org/xgl/ dapper main
deb http://ubuntu.compiz.net/ dapper main
##XMMS2
deb http://exodus.xmms.se/debian dapper main
## Listen
deb http://theli.free.fr/packages/ dapper listen

```

How do I fix this?

Thanks in advance,
Demio

---

### Post by David Corrales on 2006-09-10
Just run **sudo apt-get update** again. It was some index files missing, you should get them on the second try :)
I'd also like to point out that the first output has this line:
W: You may want to run apt-get update to correct these problems
which is the same that I have suggested.

---

### Post by Demio on 2006-09-10
Still won't work.... (same errors)

---

### Post by elettronicha on 2006-09-11
[http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) seems down, try yourself browsing it by a web browser and see. So you have to wait it returns up or contact the admin of that repository.

---

