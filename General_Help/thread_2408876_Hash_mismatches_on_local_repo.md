---
title: "Hash mismatches on local repo"
date: 2018-12-24
forum: General Help
---

### Post by jagdtigger on 2018-12-24
Hi all.

So i just reinstalled my laptop(with Lubuntu 18.10) but after i switch over to my local repo i get a bunch of errors when running "apt update":
```
Get:1 http://10.125.210.23/apt-mirror/ubuntu cosmic InRelease [242 kB]
Get:2 http://10.125.210.23/apt-mirror/ubuntu cosmic-updates InRelease [83,2 kB]
Get:3 http://10.125.210.23/apt-mirror/ubuntu-security/ubuntu cosmic-security InRelease [83,2 kB]
Get:4 http://10.125.210.23/apt-mirror/ubuntu cosmic-backports InRelease [74,6 kB]
Hit:5 http://archive.ubuntu.com/ubuntu cosmic InRelease
Hit:6 http://archive.ubuntu.com/ubuntu cosmic-updates InRelease
Get:7 http://10.125.210.23/apt-mirror/ubuntu cosmic/main amd64 Packages [1.018 kB]
Get:8 http://10.125.210.23/apt-mirror/ubuntu cosmic/main Translation-en [513 kB]
Get:9 http://10.125.210.23/apt-mirror/ubuntu cosmic/main amd64 DEP-11 Metadata [475 kB]
Get:10 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 48x48 Icons [123 kB]
Get:11 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64 Icons [238 kB]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Get:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons [29 B]
Ign:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons
Get:51 http://10.125.210.23/apt-mirror/ubuntu cosmic/universe DEP-11 64x64@2 Icons [11,9 kB]
Get:51 http://10.125.210.23/apt-mirror/ubuntu cosmic/universe DEP-11 64x64@2 Icons [11,9 kB]
Get:51 http://10.125.210.23/apt-mirror/ubuntu cosmic/universe DEP-11 64x64@2 Icons [11,9 kB]
Ign:51 http://10.125.210.23/apt-mirror/ubuntu cosmic/universe DEP-11 64x64@2 Icons
Get:55 http://10.125.210.23/apt-mirror/ubuntu cosmic-updates/main DEP-11 64x64@2 Icons [29 B]
Ign:55 http://10.125.210.23/apt-mirror/ubuntu cosmic-updates/main DEP-11 64x64@2 Icons
Ign:57 http://10.125.210.23/apt-mirror/ubuntu cosmic-updates/universe DEP-11 64x64@2 Icons
Ign:58 http://10.125.210.23/apt-mirror/ubuntu-security/ubuntu cosmic-security/universe DEP-11 64x64@2 Icons
Ign:59 http://10.125.210.23/apt-mirror/ubuntu cosmic-backports/universe amd64 DEP-11 Metadata
Ign:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons
Ign:51 http://10.125.210.23/apt-mirror/ubuntu cosmic/universe DEP-11 64x64@2 Icons
Ign:55 http://10.125.210.23/apt-mirror/ubuntu cosmic-updates/main DEP-11 64x64@2 Icons
Ign:57 http://10.125.210.23/apt-mirror/ubuntu cosmic-updates/universe DEP-11 64x64@2 Icons
Ign:58 http://10.125.210.23/apt-mirror/ubuntu-security/ubuntu cosmic-security/universe DEP-11 64x64@2 Icons
Get:59 http://10.125.210.23/apt-mirror/ubuntu cosmic-backports/universe amd64 DEP-11 Metadata [5.812 B]
Err:59 http://10.125.210.23/apt-mirror/ubuntu cosmic-backports/universe amd64 DEP-11 Metadata
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:5812 [weak]
   - SHA256:d9b33ae18aeb7ded8ffa826af01f94ca63f080f8bda3d6308524562c4fe4f382
   - SHA1:c32ab4397f512b02a3cfed88b4395dbb2bba4097 [weak]
   - MD5Sum:285347104aa385c4fd424a9b48ddc621 [weak]
  Hashes of received file:
   - SHA256:ad00c8cd9508030a7189643912f477130f9c6c0fe771a620f74492696215e868
   - SHA1:688ff8410653410670967cbbfe418729d5adf293 [weak]
   - MD5Sum:849d7d6f4d2ed09d57e223b222507ffe [weak]
   - Filesize:5812 [weak]
  Last modification reported: Sun, 23 Dec 2018 00:05:55 +0000
  Release file created at: Sun, 23 Dec 2018 04:07:36 +0000
Ign:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons
Ign:51 http://10.125.210.23/apt-mirror/ubuntu cosmic/universe DEP-11 64x64@2 Icons
Ign:55 http://10.125.210.23/apt-mirror/ubuntu cosmic-updates/main DEP-11 64x64@2 Icons
Ign:57 http://10.125.210.23/apt-mirror/ubuntu cosmic-updates/universe DEP-11 64x64@2 Icons
Ign:58 http://10.125.210.23/apt-mirror/ubuntu-security/ubuntu cosmic-security/universe DEP-11 64x64@2 Icons
Err:12 http://10.125.210.23/apt-mirror/ubuntu cosmic/main DEP-11 64x64@2 Icons
  404  Not Found [IP: 10.125.210.23 80]
Ign:51 http://10.125.210.23/apt-mirror/ubuntu cosmic/universe DEP-11 64x64@2 Icons
Err:55 http://10.125.210.23/apt-mirror/ubuntu cosmic-updates/main DEP-11 64x64@2 Icons
  404  Not Found [IP: 10.125.210.23 80]
Ign:57 http://10.125.210.23/apt-mirror/ubuntu cosmic-updates/universe DEP-11 64x64@2 Icons
Err:58 http://10.125.210.23/apt-mirror/ubuntu-security/ubuntu cosmic-security/universe DEP-11 64x64@2 Icons
  404  Not Found [IP: 10.125.210.23 80]
Fetched 489 kB in 2s (260 kB/s)
Reading package lists...
```

sources.list:
```
# Automatically generated by Calamares on 2018-12-24.
# Lines starting with "deb" are mandatory, while lines starting with "deb-src"
# are for more detailed package information.

## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of Lubuntu.
deb http://10.125.210.23/apt-mirror/ubuntu/ cosmic main restricted
# deb-src http://archive.ubuntu.com/ubuntu/ cosmic main restricted

## Major bug fix updates produced after the final release of Lubuntu.
## Have you noticed a regression? Please report it!
## https://wiki.ubuntu.com/StableReleaseUpdates#Regressions
deb http://10.125.210.23/apt-mirror/ubuntu/ cosmic-updates main restricted
# deb-src http://archive.ubuntu.com/ubuntu/ cosmic-updates main restricted

## Software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu team.
## Also, please note that software in Universe WILL NOT receive any review or
## updates from the Ubuntu security team directly. Updates in this repository
## are provided by volunteers, but most come from Debian.
deb http://10.125.210.23/apt-mirror/ubuntu/ cosmic universe
# deb-src http://archive.ubuntu.com/ubuntu/ cosmic universe
deb http://10.125.210.23/apt-mirror/ubuntu/ cosmic-updates universe
# deb-src http://archive.ubuntu.com/ubuntu/ cosmic-updates universe

## Software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu team,
## and may not be under a free licence. Please satisfy yourself as your rights
## to use the software. Also, please note that software in Multiverse WILL NOT
## receive any review or updates from the Ubuntu security team directly.
deb http://archive.ubuntu.com/ubuntu/ cosmic multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ cosmic multiverse
deb http://archive.ubuntu.com/ubuntu/ cosmic-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ cosmic-updates multiverse

## Software from this repository contains tested security updates from the
## Ubuntu security team.
deb http://10.125.210.23/apt-mirror/ubuntu-security/ubuntu cosmic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu cosmic-security main restricted
deb http://10.125.210.23/apt-mirror/ubuntu-security/ubuntu cosmic-security universe
# deb-src http://security.ubuntu.com/ubuntu cosmic-security universe
deb http://10.125.210.23/apt-mirror/ubuntu-security/ubuntu cosmic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu cosmic-security multiverse

## Software from this repository may not have been tested as extensively as
## software contained in the main release, although it includes newer versions
## of some applications which may provide useful features. Also, please note
## that software in Backports WILL NOT receive any review or updates from the
## Ubuntu security team.
deb http://10.125.210.23/apt-mirror/ubuntu/ cosmic-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ cosmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## "partner" repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu cosmic partner
# deb-src http://archive.canonical.com/ubuntu cosmic partner
```

mirror.list:
```
# apt-mirror configuration file

##
## The default configuration options (uncomment and change to override)
##
#
 set base_path           /mnt/apt-mirror/
# set mirror_path  $base_path/mirror
# set skel_path           $base_path/skel
# set var_path     $base_path/var
#
# set defaultarch
# set nthreads     20
#

#Debian 9
deb-amd64 http://deb.debian.org/debian stretch main
deb-amd64 http://security.debian.org/debian-security/ stretch/updates main
deb-amd64 http://deb.debian.org/debian stretch-updates main
deb-amd64 http://deb.debian.org/debian stretch main contrib non-free
deb-amd64 http://security.debian.org/debian-security/ stretch/updates main contrib non-free
deb-amd64 http://deb.debian.org/debian stretch-updates main contrib non-free

deb-i386 http://deb.debian.org/debian stretch main
deb-i386 http://security.debian.org/debian-security/ stretch/updates main
deb-i386 http://deb.debian.org/debian stretch-updates main
deb-i386 http://deb.debian.org/debian stretch main contrib non-free
deb-i386 http://security.debian.org/debian-security/ stretch/updates main contrib non-free
deb-i386 http://deb.debian.org/debian stretch-updates main contrib non-free


#Ubuntu bionic
###### Ubuntu Main Repos
deb-amd64 http://archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse


###### Ubuntu Update Repos
deb-amd64 http://security.ubuntu.com/ubuntu bionic-security main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu/ bionic-security main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse


deb-i386 http://security.ubuntu.com/ubuntu bionic-security main restricted universe multiverse
#deb-i386 http://archive.ubuntu.com/ubuntu/ bionic-security main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse


###### Ubuntu Partner Repo
deb-amd64 http://archive.canonical.com/ubuntu bionic partner
deb-i386 http://archive.canonical.com/ubuntu bionic partner


###### Ubuntu Extras Repo
#deb http://extras.ubuntu.com/ubuntu bionic main


#Ubuntu 
###### Ubuntu Main Repos
deb-amd64 http://archive.ubuntu.com/ubuntu/ cosmic main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu/ cosmic main restricted universe multiverse


###### Ubuntu Update Repos
deb-amd64 http://security.ubuntu.com/ubuntu cosmic-security main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu/ cosmic-security main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu/ cosmic-updates main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu/ cosmic-proposed main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu/ cosmic-backports main restricted universe multiverse


deb-i386 http://security.ubuntu.com/ubuntu cosmic-security main restricted universe multiverse
#deb-i386 http://archive.ubuntu.com/ubuntu/ cosmic-security main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu/ cosmic-updates main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu/ cosmic-proposed main restricted universe multiverse
deb-i386 http://archive.ubuntu.com/ubuntu/ cosmic-backports main restricted universe multiverse


###### Ubuntu Partner Repo
deb-amd64 http://archive.canonical.com/ubuntu cosmic partner
deb-i386 http://archive.canonical.com/ubuntu cosmic partner


###### Ubuntu Extras Repo
#deb http://extras.ubuntu.com/ubuntu cosmic main


#Raspbian
deb-armhf http://raspbian.raspberrypi.org/raspbian/ stretch main contrib non-free rpi
deb-armhf http://archive.raspberrypi.org/debian/ stretch main ui


#Wine
deb-amd64 https://dl.winehq.org/wine-builds/ubuntu/ artful main
deb-i386 https://dl.winehq.org/wine-builds/ubuntu/ artful main

#MESA
deb-amd64 http://ppa.launchpad.net/paulo-miguel-dias/pkppa/ubuntu bionic main
deb-i386 http://ppa.launchpad.net/paulo-miguel-dias/pkppa/ubuntu bionic main


deb-amd64 http://ppa.launchpad.net/paulo-miguel-dias/mesa/ubuntu bionic main
deb-i386 http://ppa.launchpad.net/paulo-miguel-dias/mesa/ubuntu bionic main

#Wine Ubuntu 18.10
deb https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard ./

```
apt-mirror is running on RPI2(raspbian), storage is provided by my NAS over NFS.

I just run a manual apt-mirror but it executes without errors.

Have someone an idea where should i start?

Thanks in advance.

---

### Post by jagdtigger on 2018-12-25
Okay it seems the hash errors gone now but i cant install anything unless i remove the 50appstream file from apt.conf.d......

---

