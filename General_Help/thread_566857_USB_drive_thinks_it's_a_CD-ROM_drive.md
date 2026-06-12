---
title: "USB drive thinks it's a CD-ROM drive"
date: 2007-10-03
forum: General Help
---

### Post by ManOnOneWheel on 2007-10-03
My friend got a USB thumbdrive for free (i don't know where he got it) and now wants it formatted to doubly be sure it doesnt have any kind of weird viruses on it (he is a windows user). I figured easy job, right? I plug in the USB and it auto mounts . .  as a CD-ROM drive? It has some funky autorun.inf on it. I tried using GParted, but it didnt see the drive, neither did fdisk -lu. It is detected in lsusb, but just with a number. Is there another way to format this crazy thing?

---

### Post by sune_cph on 2007-10-04
> **ManOnOneWheel said:**
> My friend got a USB thumbdrive for free (i don't know where he got it) and now wants it formatted to doubly be sure it doesnt have any kind of weird viruses on it (he is a windows user). I figured easy job, right? I plug in the USB and it auto mounts . .  as a CD-ROM drive? It has some funky autorun.inf on it. I tried using GParted, but it didnt see the drive, neither did fdisk -lu. It is detected in lsusb, but just with a number. Is there another way to format this crazy thing?

Probably it's a U3 drive, ie. has a "read-only" drive that pretends to be a CD-ROM plus a normal writeable storage area. Most U3 drives come with (Windows) utilities that allow you to remove the CD-ROM part if that's what you want. Not sure if you can do it from Linux though.

/Sune

---

### Post by ManOnOneWheel on 2007-10-04
Hmm, i'll give that a try, if i can find the windows utilities.

---

