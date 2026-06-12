---
title: "No proprietary software listed - huh?"
date: 2006-10-26
forum: General Help
---

### Post by Aranel on 2006-10-26
Hey. I just installed Edgy today (a clean install - I'd been using Debian Sarge previously), and I'm really liking it... but I'm having some problems. First of all, I want to install Mercury Messenger, which needs a Java virtual machine to run. Synaptic Package Manager can't find any corresponding packages, though, and upon further investigation, it looks like it can't find any other proprietary software either (Acrobat Reader, the Flash plugin, Opera, RealPlayer, w32 codecs, etc.).

All of these *are*, however, given as options in Applications > Add/Remove. But when I try to check one, I get a very strange error (see attachment).

This is my sources.list:

> # 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

Is there a repository I haven't added? Were these packages in the former PLF repository or something? I'm sort of new to Ubuntu itself, though a bit more familiar with Debian-like stuff, so... any explanations would be appreciated.

---

### Post by dmb on 2006-10-26
Do you have a 64bit proccesor and install the 64bit version of ubuntu? If so,  you have to do some special things to get it to work.

---

### Post by shinythings on 2006-10-26
You'll need the 'multiverse' reprositories. Just add 'multiverse' to the two lines in the 'universe' section.

---

### Post by Aranel on 2006-10-26
> **shinythings said:**
> You'll need the 'multiverse' reprositories. Just add 'multiverse' to the two lines in the 'universe' section.

...Wow. That was easy. Thanks a bunch! :D

---

### Post by rocknrolf77 on 2006-10-26
Take a look at [www.ubuntuguide.org](www.ubuntuguide.org)  There you can find a lot of stuff that is nice to learn.

---

### Post by glotz on 2006-10-26
And should you want to get rid of proprietary software, get vrms! [http://packages.debian.org/stable/admin/vrms](http://packages.debian.org/stable/admin/vrms) :)

One version is also in the repos.

---

