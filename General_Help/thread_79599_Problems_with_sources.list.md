---
title: "Problems with sources.list"
date: 2005-10-20
forum: General Help
---

### Post by Einaras on 2005-10-20
Hi, what's wrong with my source.list ?
```
root@Picius:/home/einaras# apt-get update
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://security.ubuntu.com breezy-security Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Hit http://security.ubuntu.com breezy-security Release
Get:3 http://se.archive.ubuntu.com breezy Release.gpg [189B]
Get:4 http://se.archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:5 http://se.archive.ubuntu.com breezy Release [30.9kB]
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Get:6 http://se.archive.ubuntu.com breezy-updates Release [19.6kB]
Get:7 http://security.ubuntu.com breezy-security/main Packages [14B]
Hit http://security.ubuntu.com breezy-security/restricted Packages
Get:8 http://security.ubuntu.com breezy-security/main Sources [14B]
Hit http://security.ubuntu.com breezy-security/restricted Sources
Get:9 http://security.ubuntu.com breezy-security/universe Packages [14B]
Hit http://security.ubuntu.com breezy-security/universe Sources
Get:10 http://se.archive.ubuntu.com breezy/main Packages [585kB]
Get:11 http://se.archive.ubuntu.com breezy/restricted Packages [5061B]
Get:12 http://se.archive.ubuntu.com breezy/main Sources [232kB]
Get:13 http://se.archive.ubuntu.com breezy/restricted Sources [1454B]
Get:14 http://se.archive.ubuntu.com breezy/universe Packages [2304kB]
Get:15 http://se.archive.ubuntu.com breezy/universe Sources [915kB]
Get:16 http://se.archive.ubuntu.com breezy-updates/main Packages [13.2kB]
Get:17 http://se.archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:18 http://se.archive.ubuntu.com breezy-updates/main Sources [3286B]
Get:19 http://se.archive.ubuntu.com breezy-updates/restricted Sources [14B]
Fetched 4110kB in 15s (266kB/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz  MD5Sum mismatch
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz  MD5Sum mismatch
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz  MD5Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by mtron on 2005-10-20
seems like the server you are downloading from is just updating or you encountered a download problem try sudo apt-get update again, and if you get the same results post your /etc/apt/sources.list file here.

---

### Post by Einaras on 2005-10-20
Did apt-get update 10 times :D and same shit :D
Here's the sources.list :
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://se.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://se.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://se.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://se.archive.ubuntu.com/ubuntu breezy universe
deb-src http://se.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

```

---

