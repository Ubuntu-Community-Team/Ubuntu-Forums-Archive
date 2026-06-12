---
title: "Installed Edgy: how to play mp3's?"
date: 2006-10-27
forum: General Help
---

### Post by bg1256 on 2006-10-27
My notebook runs Ubuntu, and I used Automatix to install the codecs I needed.

When I try to play MP3's on Edgy on my desktop, I'm unable.

Is there a simple way to solve this?

---

### Post by Fass on 2006-10-27
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by bg1256 on 2006-10-27
alright, thanks!

---

### Post by charles_elwood on 2006-10-27
Where has libxine-extracodecs gone?

---

### Post by Fass on 2006-10-28
> **charles_elwood said:**
> Where has libxine-extracodecs gone?

It hasn't gone anywhere. It's right there in multiverse.

---

### Post by charles_elwood on 2006-10-28
Yes, it is the multiverse that disappeared from sources.list. Somewhere amongst the upgrade it got reset. Joy.

---

### Post by dolarsrg on 2006-11-03
I've this sources.list:

```

deb http://es.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://es.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://es.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://es.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://es.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

am I missing some multiverse repository? I've run sudo apt-get update and when libxine-extracodecs it tells me "The package is not avalible but some other packages are linking it" or something similar in my language.

I've found the package in packages.ubuntu.com but I'd like to know where can I find the official and complete repository list.

Thanks a lot ;)

---

### Post by charles_elwood on 2007-12-03
A bit late but you only have multiverse enabled for the backports section, so yes, you're missing some. You need to enable multiverse on releasename as well as releasename-updates and releasename-backports

---

