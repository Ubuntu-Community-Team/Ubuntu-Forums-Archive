---
title: "Problems with USB external hard drive"
date: 2012-11-07
forum: General Help
---

### Post by orentsur on 2012-11-07
Hi all,

I hope I am posting in the right place...  

I have a spare 2.5" HDD after I upgraded my laptop's hard drive.  It is in perfect working order and has been tested successfully.  No bad sectors or any other funnies... I thought I would use the spare drive as a back-up external drive.  I purchased an enclosure planted the drive in and then went about formatting the drive with GParted.  Al went well. GParted recognises the drive (sdb1) and will accept any operation I choose, i.e. delete the partition, create a new partition etc.  However, as soon as the operations have completed successfully and GParted mounts the device again, the new partition is showing as unallocated space. Further operations are only possible after creating a new partition table. I tried to format it as FAT32, NTFS, EXT4.  The result is always the same.

Next I formatted the drive using the family's windows PC.  Windows will happily format and use the external drive (NTFS).  As soon as I connect it to my laptop, Xubunut does not mount the drive. 

So next, I purchased a different enclosure.  Same problem.
USB memory sticks work perfectly.

Any ideas?

Thanks for looking...

---

### Post by hal8000 on 2012-11-07
Plug in the external hard drive and post output of:


sudo fdisk -l

(last character lowercase "L")

As its showing as /dev/sdb1 there is only one partition. You should be able to create a partition with linux fdisk or cfdisk.

I can only think that sdb1 is not using the full amount of sectors on your drive which is why there is unpartitioned space.

---

### Post by orentsur on 2012-11-14
Thanks for replying.  Here is the output after another try of formatting the drive:
/dev/sdb1              63   312576704   156288321    c  W95 FAT32 (LBA)

The funny thing is that, as I mentioned, I formatted the drive with my Windows PC to NTFS.  I then transferred some files to it for testing...  then plugged the drive to my Ubuntu machine. It mounted fine, I managed to see what's on it.  Then, as soon as I safely removed the drive, whatever was on it disappeared.  So the drive mounted successfully on Windows and Ubuntu but the contents simply vanished....  Decided to format again and that's it.  The drive will not mount and won't format.

:(

---

### Post by orentsur on 2012-11-16
....and another update!  With a LIVE CD, it all works 100% right!!! 
:confused: :confused: :confused: :confused: :confused:

---

