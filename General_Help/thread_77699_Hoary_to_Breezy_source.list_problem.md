---
title: "Hoary to Breezy source.list problem"
date: 2005-10-17
forum: General Help
---

### Post by Lunatik on 2005-10-17
Hi, I have been trying to follow all the "how-to"s I could find to upgrade from Hoary to Breezy, they all tell me to edit my sources.list, and replace the "hoary" string for "breezy".

The only problem I got is this repository.

> ##Kubuntu
deb [http://kubuntu.org/hoary-kde342/](http://kubuntu.org/hoary-kde342/) hoary-updates main
deb-src [http://kubuntu.org/hoary-kde342/](http://kubuntu.org/hoary-kde342/) hoary-updates main

What is the replacement repository for this one? I tried
> ##Kubuntu
deb [http://kubuntu.org/breezy-kde342/](http://kubuntu.org/breezy-kde342/) breezy-updates main
deb-src [http://kubuntu.org/breezy-kde342/](http://kubuntu.org/breezy-kde342/) breezy-updates main
and
> ##Kubuntu
deb [http://kubuntu.org/breezy-kde343/](http://kubuntu.org/breezy-kde343/) breezy-updates main
deb-src [http://kubuntu.org/breezy-kde343/](http://kubuntu.org/breezy-kde343/) breezy-updates main

and few others, but I couldn't get this to work. Could anyone post a Kubuntu Breezy sources.list please?

EDIT : Changed source.list to sources.list

---

### Post by Triton on 2005-10-17
This is what I have:

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted 


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe 
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by derrick1985 on 2005-10-17
These two lines:

 ##Kubuntu
deb [http://kubuntu.org/breezy-kde342/](http://kubuntu.org/breezy-kde342/) breezy-updates main
deb-src [http://kubuntu.org/breezy-kde342/](http://kubuntu.org/breezy-kde342/) breezy-updates main

 ##Kubuntu
deb [http://kubuntu.org/breezy-kde343/](http://kubuntu.org/breezy-kde343/) breezy-updates main
deb-src [http://kubuntu.org/breezy-kde343/](http://kubuntu.org/breezy-kde343/) breezy-updates main

Are NOT NEEDED because 5.10 already has KDE 3.4.3, so those repositories are not needed.

This is my sources.list file as well, use this when dist-upgrade'ing


# deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Backports
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted


Notice backports for now is commented out, simply because there are none.

---

### Post by Lunatik on 2005-10-17
Thanks!

---

