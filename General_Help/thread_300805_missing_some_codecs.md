---
title: "missing some codecs"
date: 2006-11-16
forum: General Help
---

### Post by komaroveli on 2006-11-16
hi all,
following wiki page on multimedia i tryed to install all multidedia codecs without automatix2 or easyubuntu. but i couldn't install some of them, like libxine-extracodecs for example, or gstreamer10-bad-multiverce (i have gstreamer10-bad)...could you help? i have been searching forum and net for couple hours now.....
this is my source.list:
```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf edgy-plf free non-free
deb-src http://packages.freecontrib.org/plf edgy-plf free non-free  


```

thnx in advance

---

### Post by komaroveli on 2006-11-16
anyone?

---

### Post by strabes on 2006-11-16
what do you mean 'it couldn't install some of them' did it say the packages weren't found or were there dependency problems (unlikely)

what guide are you following? try this page: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

hope this helps

---

### Post by komaroveli on 2006-11-16
i followed exact same guide...and for example for libxine-extracodecs i get following:
```
nico@nico-desktop:~$ sudo apt-get install libxine-extracodecs
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine-extracodecs has no installation candidate
nico@nico-desktop:~$

```
so ... as far as i understood there is no such package!
...
any other ideas?

PS these packages i'm missing:
libxine-extracodecs
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly-multiverse

---

### Post by rattlertech on 2006-12-05
I'm having the exact same problem as komaroveli.

```

rattlertech@(Box name):~$ sudo apt-get install libxine-extracodecs
Reading package lists... Done
Building dependency tree... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine-extracodecs has no installation candidate
rattlertech@(Box name):~$ 

```

I'm running on Kubuntu right now. Could that have something to do with it? All help appreciated.

---

### Post by mgmiller on 2006-12-05
I believe they are all in multiverse, which you do not have enabled.  The easiest way is to add them to your universe lines.

Change this:
```
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe
```

To this:
```
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe multiverse

```

Then do a sudo apt-get update.  You should then be able to add the packages you need.

---

### Post by rattlertech on 2006-12-05
EDIT: Issue resolved due to a hard night of googling. Thanks mgmiller. I had to enable multiverse.

---

