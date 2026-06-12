---
title: "kde4 rc2 install gone wrong"
date: 2007-12-20
forum: General Help
---

### Post by laugurinn on 2007-12-20
followed the kde4 rc2 instructions (installed kde first on top of ubuntu and then kde4).

now getting this error in synaptic:

E: /var/cache/apt/archives/kdebase-runtime-bin-kde4_4%3a3.97.0-1ubuntu5~gutsy1~ppa3_all.deb: trying to overwrite `/usr/bin/kdebugdialog', which is also in package kdebase-bin

semi-noob here btw but any ideas?

---

### Post by mifly on 2007-12-21
I had the same problem.But now ,I fix it.
I found the installed k3b depends kdebase-bin,so i remove them:
> sudo dpkg -P kdebase-bin k3b
then
>  sudo apt-get -f install
maybe this help you

---

