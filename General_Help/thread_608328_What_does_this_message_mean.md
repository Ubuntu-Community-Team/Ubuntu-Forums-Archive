---
title: "What does this message mean?"
date: 2007-11-09
forum: General Help
---

### Post by enchance on 2007-11-09
I sometimes get this message before booting up in gutsy
```
drive/hda1 has been mounted 30 times without being checked, check enforced
```
something like that. If it's not hda1 it's hda2. Is gutsy telling me something?

---

### Post by dpar on 2007-11-09
It's just checking the disk for errors.Kind of like an automatic defrag.
Or chkdisk, I mean.

---

### Post by jflaker on 2007-11-09
> **enchance said:**
> I sometimes get this message before booting up in gutsy
```
drive/hda1 has been mounted 30 times without being checked, check enforced
```
something like that. If it's not hda1 it's hda2. Is gutsy telling me something?

drives are addressed from 0....this is stating the SECOND drive has been mounted /dismounted 30 times and was never checked for errors and Linux is no longer allowing you to access this drive without first making sure of the drive's integrity.  This check limits data loss.

Is this a USB drive by the way?

---

### Post by enchance on 2007-11-09
I don't think so since I don't have mine attached right now. My partitions are /, /home, swap. So it's a good thing, right? Nothing I should get paranoid about? I'm just overly conscious of keeping my ubuntu installation as clean as possible.

---

### Post by dpar on 2007-11-09
No, don't worry, it's a good thing:)

---

### Post by yabbadabbadont on 2007-11-09
It's perfectly normal.  Don't worry about it.  :D

Edit: Too slow.

---

### Post by omrsafetyo on 2007-11-09
Yeah - this is just a maintenance thing... ensuring that your hd partition is up to snuff (in this case, your master IDE HD, on partitions 2 & 3 = hda1 & hda2 respectively).

Just get worried when it tells you that an inode has become corrupted.. or etc.  The first time you deal with that, its a bit confusing - but ends up being easy.  Just follow the directions on screen, and run the fsck command manually, with the options it gives you.  Its self explanatory.  

> Is this a USB drive by the way?  This is an PATA IDE drive on  the primary channel on the the IDE0 cable.  

hd = PATA IDE
sd = SATA
usbdisk = USB

a, b, c = channel physical drive

0, 1, 2 ,3 etc. = logical partition

not sure how the naming convention differs on usb... but from my experience, usb storage is mounted as usbdisk - the others are standard though.

---

