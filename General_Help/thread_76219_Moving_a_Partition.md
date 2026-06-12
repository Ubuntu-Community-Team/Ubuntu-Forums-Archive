---
title: "Moving a Partition?"
date: 2005-10-14
forum: General Help
---

### Post by NMUrugbysteve on 2005-10-14
I messed up a bit when I installed breezy a while a go and now I have a shrinking root partition and a unnecessarily large home partition. Now I've managed to change the size of the home partition and i have 3 more gigs of free un-partition space, but I can't get the home partition to move, even when using Knoppix. Anyone know how to change the placement of a partition with Knoppix or anyother live cds? Thanks in advance.

---

### Post by manicka on 2005-10-14
You could try using gparted

sudo apt-get install gparted

---

### Post by NMUrugbysteve on 2005-10-15
Well, I've tried to use Gparted, but you can't work with mounted partitions and this laptop only has one hdd. I used gparted in the live cd, but still can't move my partitions, i can only resize them over and over.

---

### Post by az on 2005-10-15
Right, you cannot change the partition on a disk that has something mounted on it.  Also, parted cannot change the start of a partition.  It can copy it, though.

Depending on how much stuff you have on it, you can safely do some acrobatics to get the job done...

---

### Post by tagra123 on 2006-03-19
I had trouble getting ubuntu to install on a windows machine and this software got it working for me. 

It looks like it will easily let you resize partitions too.  I left grub take over but this  looks as though it will also replace grub if you want it too.

[http://www.terabyteunlimited.com/kb/category.php?id=20](http://www.terabyteunlimited.com/kb/category.php?id=20)

---

### Post by bricedebrignaisplage on 2006-05-09
parted cannot move the beginning of a partition (at least as far as I know).
As Azz said, the solution is to free enough space on the disk and then do a lot of copy, paste, delete, and so on. Not very convenient and it takes a long time to copy a partition of a few GB, so what about huge partitions...
But it has to be likewise, I mean data has to be copied from a place to another if you want to move it. However it would have been nice if parted developpers had automated the process. Or at least don't put a "move" icon so we don't loose hours figuring what's going wrong and why we cannot do it...

---

