---
title: "&quot;Read only file system&quot;"
date: 2006-11-27
forum: General Help
---

### Post by Morientes on 2006-11-27
I just installed the w32codecs package in kubuntu 6.10 but after installing it complained that it couldn't delete some files...it said something about "read only file system"...I tried playing the file that I wanted to play with the codecs and it did play, but it popped up with other warnings about "read only file system" again. It also said it when I tried other files.
I tried to reinstall the codecs pack again - this time it said "bus error". After a reboot everything seems to be fine.

Anyone know what happened?

---

### Post by CatKiller on 2006-11-27
If you'd like some wanton speculation, two things that I can think of are either that you can't write to the filesystem because of permissions problems, or that because of problems with that filesystem it had been remounted as read-only so that nothing else got broken.

---

### Post by Morientes on 2006-11-28
Hm ok thanks.

I think it has to do with the generally bad support of core 2 duo processors in the generic kernel.

Does anyone know when a new kernel might come out? Right now I have got my system running by passing the parameters noapic nolapic irqpoll acpi=off pci=noacpi to the kernel at startup, but seeing that something like this can happen, there must still be problems (I am pretty sure my hardware is fine).
Could one install another kernel - any ideas as to which kernel I might switch to that would increase my stability?

---

