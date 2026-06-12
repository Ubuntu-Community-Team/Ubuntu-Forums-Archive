---
title: "Can't burn full DVDs with nautilus"
date: 2007-08-01
forum: General Help
---

### Post by altenor on 2007-08-01
Hi everyone !

I've been using Ubuntu for a year or so, and enjoying it very much so far !

There is one thing I haven't been able to solve by myself yet : burn full 4,4GB dvds with nautilus.

The problem is nautilus writes an ISO image file on the hard drive before burning the dvd. However the maximum size of a linux file is 4GB, which is lower than the size of a dvd. Thus the writing of the image file crashes at 4GB of data, and I can't burn the dvd at all.

Has anyone found a way around this ?

Thanx,
Vincent

---

### Post by AnRa on 2007-08-01
The maximum file size with Ext3 is at least 16GiB (it depends on the block size) so that couldn't be the problem.

Did you try with K3b or any other program?

---

### Post by altenor on 2007-08-01
Yes you're right.

I forgot that the partition nautilus writes the image file to is a FAT 32 one. The 4GB limit must come from windows file system, not linux's... :-(

My machine has a dual boot with a 6.5GB partition for Linux, one NTFS partition for windows, and one 58GB FAT 32 partition to share files between the 2 OS.

The linux partition only has 2.2 GB left, not enough to write the DVD image file on.

Is it still possible to burn DVDs somehow with these partitions, or do I have to resize them?

Thx

---

### Post by stchman on 2007-08-01
> **altenor said:**
> Yes you're right.

I forgot that the partition nautilus writes the image file to is a FAT 32 one. The 4GB limit must come from windows file system, not linux's... :-(

My machine has a dual boot with a 6.5GB partition for Linux, one NTFS partition for windows, and one 58GB FAT 32 partition to share files between the 2 OS.

The linux partition only has 2.2 GB left, not enough to write the DVD image file on.

Is it still possible to burn DVDs somehow with these partitions, or do I have to resize them?

Thx

6.5GB is way too small for Linux.  I give my Linux at least 20GB.  Give Ubuntu more space.

Also install K3B with the mp3 plugin.

---

### Post by AnRa on 2007-08-01
K3b is able to burn without creating image files first. ;)

---

