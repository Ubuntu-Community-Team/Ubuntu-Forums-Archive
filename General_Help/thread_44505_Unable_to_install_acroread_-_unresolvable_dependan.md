---
title: "Unable to install acroread - unresolvable dependancy issue"
date: 2005-06-26
forum: General Help
---

### Post by alexhawdon on 2005-06-26
Having trouble installing acroread on my new Hoary install.  

Install is fresh as of yesterday and I've done nothing special with it other than blindly add a few repos as suggested in the unofficial ubuntu guide to allow me to install small amounts of software and libs (dvdcss, the usual post-install linux stuff).  

In trying to rectify the issue I learnt a little about the sources.list file and have cleaned it up a bit so it now reads;
----------------------------------------------
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
---------------------------------------------

All software is being installed using Synaptic.  The error message I'm getting is;

acroread:
  Depends: libgcc1 (>=1:4.0.0-7) but 1:4.0-0pre6ubuntu7 is to be installed

Any ideas anyone?  Any hints as to why I might be experiencing this when nobody else seems to be?

Thanks and Regards,

Alex

---

### Post by Leif on 2005-06-26
Add

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted

to your sources as well.

---

