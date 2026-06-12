---
title: "ssh speed and multiverse in edgy"
date: 2006-10-30
forum: General Help
---

### Post by viz_e on 2006-10-30
Hi.
Upgrading to edgy I solved many problems that I had with dapper. IMHO edgy rules!!

I just have two problem I would like to address:

* Copying files with scp is slow: I get 1.2 Mbytes/s in upload and 1.6 Mbytes/s in download. Dapper was 10 times faster.
The CPU is not used very much and downloading files from the Internet is fast. What's wrong?

* I cannot install packages from multiverse. This is an example:

```
sudo apt-get install realplayer
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate
```

This is my sources.list file:

```
cat /etc/apt/sources.list

deb http://ch.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ch.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in


## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ch.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://ch.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ch.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
```

Any help is appreciated. Thank you Kubuntu team! :KS

---

### Post by frying_fish on 2006-10-30
you only have backports with a multiverse option, you need to enable multiverse for more than just backports to be able to get them from elsewhere.

---

