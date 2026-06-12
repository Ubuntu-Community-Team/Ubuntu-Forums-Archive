---
title: "Ubuntu seems to have locked my USB drive"
date: 2012-11-25
forum: General Help
---

### Post by MikeSz on 2012-11-25
Hi All - I have just got hold of a friends external usb hard-drive, a little samsung 1tb 2.5incher.  His provisio was that I backed up the stuff before using it as he had some work on there.  So...I plugged the drive into my ubuntu laptop as it has a large hard disk, copied his folder on to my laptop with the intention of then plugging the drive into my intel imac so that I could wipe it, back that up and then reinstall a new operating system there (just got a newer version so needed to back up my itunes)

So - Ive backed up my mates files, safely removed and ejected this hard drive (I didnt just yank it out) and gone to plug it into my mac however my mac says that the drive is "restricted" and is seemingly read only.  

Its an NTFS drive as my mate uses windows (I didnt think it would matter what he used) though I have a feeling Ubuntu has now decided to 'own' it.  This is a bit of a problem as I need to back my stuff up, do what I need to do, restore his drive to how it was and give it back to him!!

Anyone know how I can 'unlock' this drive again in simple to follow 'idiot's  guide' style?  Its still hooked up to my ubuntu laptop at the moment which is running (I think) 12.04

---

### Post by mcduck on 2012-11-25
Ubuntu didn't "lock your drive". :D

The problem is simply that OS X doesn't support writing to NTFS file system. Since you are planning on using it to back up your mac, just plug it in to the machine, and use it's disk tools to reformat the drive to HFS+.

(formatting to FAT would also work, but since HFS+ is native filsesystem for your mac, it allows maintaining file permissions and other extra information.)

---

### Post by MikeSz on 2012-11-25
Phew, thanks for that!!  I only assumed that it had locked it as Ive had that before with memory sticks where ive used them on my ubuntu machine then cant use them on anything else (unless its the same issue) So just figured id somehow mounted this one and then locked it by mistake.  

Thanks for your help and Il now crack on!!!

---

