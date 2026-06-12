---
title: "removing xserver and going to native shell"
date: 2006-11-27
forum: General Help
---

### Post by qtronix on 2006-11-27
hi guys, 

my upgrade procedure was from ubnutu 5.10 > xubuntu (desktop) > xubuntu 6.06.1 (via "update-manager -d"). 

My question is, that the use of this server is now changing, and now I don't need X (or any desktop manager even). The only need is now to become a samba file server, and a mail hub. All i need is this now ubuntu 6.06.1 be in command line interface all the time, and remove unnecessary packages to conserve disk space.

Is there anyway to completely remove X, gnome, etc? I've been going through the packages one-by-one but its kinda tiresome. Thanks.

---

### Post by cilynx on 2006-11-27
Getting rid of xorg, x-window-system, and x-window-system-core should do pretty well.  Any stragglers you'll have to do by hand.
```
sudo apt-get remove xorg* x-window-system*
```
My system tells me that I'll get back ~160M with those removed.

---

