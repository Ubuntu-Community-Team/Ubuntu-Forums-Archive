---
title: "Running Ubuntu [Edgy] on Flash Memory"
date: 2006-11-10
forum: General Help
---

### Post by blueshadowX on 2006-11-10
Hi.  I've learned that it is feasible to install Ubuntu onto a flash memory device such as a Compact Flash card.  However, I've also read that due to the limited read/write cycles for flash memory, it is not a good idea to install a full operating system onto a flash memory device without using some sort of a read/write filter or a ramdisk.  Is there a simple way I could have ubuntu do read/write on a fake ramdisk, then have it periodically flush the data to disk?  Thanks.

---

### Post by kerry_s on 2006-11-10
Ubuntu i don't know, but DSL linux is made to do that and is only 50mb to start.-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by K.Mandla on 2006-11-10
> **kerry_s said:**
> Ubuntu i don't know, but DSL linux is made to do that and is only 50mb to start.-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)
Yup, DSL is the place to start with this idea. Their Frugal Installs to CF card are the stuff of legend.

If I recall correctly, they have startup and shutdown scripts that more or less do exactly what you're thinking. I think they also set up a ramdisk for "swap" (which always sounded counterintuitive to me), thereby saving the card from unnecessary writes. 

Have fun!

---

### Post by blueshadowX on 2006-11-10
Thanks guys.  I understand that DSL can do all of this stuff, I've already used it a long time ago, but I'll still be looking for a way to get similar scripts for ubuntu.

---

### Post by jaripetteri on 2007-01-27
Have you find a way to run ubuntu from CF? I could like to try that to. I have ubuntu mythtv-frontend-surfboard-mediaplayer-laptop with noisy hard drive and I like to swap that to complete silent CF... Or could I boot from network? I have WLAN and server on intranet I could use.

OK I could buy a new HD but thats not the point. =)

---

### Post by blueshadowX on 2007-01-27
Actually, I've realized that for the most part, running OSes on flash memory is a bad idea unless you implement some sort of write-filter.  This is because flash memory degrades awrfully quickly if you let your OS have unrestricted random access.

---

