---
title: "Please take a look at my sources.list"
date: 2005-10-23
forum: General Help
---

### Post by Krmzn on 2005-10-23
Hi guys,

Need some help regarding my sources.list file:

I cant find the unofficial packages, like fluxbox, VLC and stuff. What do I need to add into sources.list to find all the "unofficial" packages?

Here is my file:
```

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://no.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://no.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu breezy-updates main restricted universe
deb-src http://no.archive.ubuntu.com/ubuntu breezy-updates main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://no.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://no.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://no.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://no.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe


```

Thanks a lot :)

---

### Post by GoldBuggie on 2005-10-23
Please uncomment the two liknes containing
*[http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy*
[LEFT]then at the and of those lines you can also att *multiverse* so that you get access to everything.

after the changes to a reload in synaptic or a *sudo apt-get update* in the konsole

/me waves to norway
[/LEFT]

---

### Post by Krmzn on 2005-10-23
Tjena Goldbuggie :)

Thanks for the help :D That sortet it all! :)

/me waves back to Sweden

---

### Post by Heliix on 2005-10-24
hi form czech republic
i messed up my sources.list.. so thanks very much for this help
that works for me too :-)
heliix

---

