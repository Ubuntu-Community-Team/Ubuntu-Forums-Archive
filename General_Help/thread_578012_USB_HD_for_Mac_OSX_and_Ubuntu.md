---
title: "USB HD for Mac OSX and Ubuntu"
date: 2007-10-16
forum: General Help
---

### Post by taggat on 2007-10-16
I just bought a 500GB Seagate FreeAgent  USB 2 harddrive 
Is there any format that both Ubuntu and Mac OSX 10.3.9 can have read/write ability?

---

### Post by hardyn on 2007-10-16
without using drivers, fat32... I know i will get flamed for this.
if you wish to use drivers with windows, ext3

I don't recommend the use of drivers, but the call is yours.  fat32 is inefficient, but i have used it with no trouble with all my external drives.

edit: for some reason i thought windows was in your list :oops: ext3 should work for both.

---

### Post by taggat on 2007-10-16
With FAT32 the mac says it can't read the drive and wants to reformat it

---

### Post by hardyn on 2007-10-16
are you sure?  i have done it with mine.  and a friend of mine does it regularily.

how did you create the partitions and filesystem?

---

### Post by taggat on 2007-10-17
I solved it the crappy way.
I just formated it half HFS and half ext3 
I'll just copy the info off the Mac which can only see the HFS and plug it into the Dell which can see both but only write to the ext3 then move the files on the HFS to the ext3 and then finally live repartition the drive so the ext3 covers the whole drive.

---

### Post by sheck on 2007-10-17
Why don't you use NTFS.

As far as I know everything reads and writes it.

---

