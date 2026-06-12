---
title: "partitions."
date: 2008-02-14
forum: General Help
---

### Post by StOoZ on 2008-02-14
I have one H.DD installed, splitted to two NTFS partitions, 20GB for Windows around 90GB for Stuff on another partition, and only 1.5GB for linux installation.
is there any way to add an extra 20GB from the 90GB NTFS partition to the 1.5GB EXT2 ubuntu installtion partition?

10x

---

### Post by johnn1949 on 2008-02-14
The simplest solution would be to choose the resize existing 90 GB partition and install Ubuntu in the free space and ignore the 1.5 GB partition.  When it asks what size you want the new partition it means the size of the NTFS partition you want when you are finished. So you would choose 70, not 20.

If you want to change the partitions Gparted live cd is capable of resizing and moving many different partition formats, but study the guide and be careful.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by StOoZ on 2008-02-14
I dont want to reinstall linux, and I dont mind about the data that is in the 90GB NTFS partition.
I do care about the current linux & Windows partitions.
so is it possible to appendix this 90GB of space to the current linux partition with that software?

---

### Post by johnn1949 on 2008-02-15
I don't beleive there is any way to just add part of one partition to another.

gparted can resize or move partitions .  for example if your first partition is 20GB windows, 2nd is 90 NTFS, and your 3rd is 1.5 ext2.  Gparted can shrink the 90GB partition to 70GB.  Shrinking moves the right  side of the partition to the left.  Then you could move the 1.5 partition to the left, and grow it to 21.5 GB.

Gparted isn't perfect but I've successfully performed similiar operations.  I certainly would be a very  hesitant to try making such a drastic change to the partitions if I didn't have a complete system back up such as Ghost or Acronis TrueIimage

---

### Post by StOoZ on 2008-02-15
ok , so let me undetstand, now my linux is installed on a partition that is 1.5GB , which is  small , there is no way I can make it bigger? (without deleting the current installation)

---

### Post by louieb on 2008-02-15
Maybe you can with GParted  
If the partitions are next to each other and of the same type (primary or logical).
and the Linux partition is to the right of the NTFS partition.
Then shrink the  NTFS partition creating unallocated space. 
Finish it up by growing the Linux partition in the now unused space.

Go to a movie or do some yard work. Its going to take GParted maybe an hour or two. Good luck.

---

### Post by StOoZ on 2008-02-16
thanks.... I'll give it a try
I already backed up all the important stuff.

---

