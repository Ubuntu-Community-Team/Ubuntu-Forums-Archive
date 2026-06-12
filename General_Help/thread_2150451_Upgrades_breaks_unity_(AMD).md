---
title: "Upgrades breaks unity (AMD)"
date: 2013-06-01
forum: General Help
---

### Post by bramr on 2013-06-01
Hi,

I'm running ubuntu 13.04 (64bit) in combination with a AMD 7950 GPU. I'm running the latest (non-beta) drivers from the amd website. 

I'm having the following problem: Every time I update via software manager op apt-get upgrade unity gets broken. After a reboot the titlebar and icon bar on the left are gone. I have searched the internet and only one thing seems to be working -> Reinstall amd drivers and run
```
dconf reset -f /org/compiz/
unity --reset-icons&disown
```

I already did this twice this week, after each upgrade. This is very annoying because i lose all my icon's + it takes me allot of time. (i'm new on ubuntu)

I'm not 100% certain if it happens after every update. I've seen that last week there where some update's on linux kernel. Maybe it only happens then? I'm new at ubuntu, it's only a wild guess.

Anyone else having this problem or knows how to fix this?

(sorry for the bad English)

---

### Post by Mark Phelps on 2013-06-01
When you install drivers from the AMD website, this is the result you make.  They are tied to a specific version of the Linux kernel when installed, and when you do an upgrade that changes that version, the drivers "break".

If you install using Additional Drivers instead, you won't have to do this.

Also, unless you need GPU temp management or hardware accelerated 3D gaming support, you don't really need the restricted AMD drivers installed.  The default Radeon drivers are more than adequate for typical desktop work.

---

### Post by bramr on 2013-06-01
Thanks, changing to default radeon drivers.

---

