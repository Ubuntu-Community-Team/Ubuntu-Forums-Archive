---
title: "partition table borked, suggestions on how to fix?"
date: 2007-04-17
forum: General Help
---

### Post by Polygon on 2007-04-17
i turned on my comp today only to be met with fsck errors. I ignored them and continued booting, and i noticed that my external drive was not mounted

i went to the gnome partition editor to find the path so i could mount it manually only to find the entire partition table gone

it had a ntfs, ext3 and fat 32 partitons on it

is there any suggestions on how i might go recovering the stuff on it? I tried testdisk but it could not find the partitions. 

and here is the output from fdisk -l

> 
mark@ubuntu:~$ fdisk -l

Disk /dev/hda: 100 MB, 100663296 bytes
64 heads, 32 sectors/track, 96 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda4   *           1          96       98288    6  FAT16

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table
mark@ubuntu:~$ 



---

### Post by amohanty on 2007-04-17
Hope you backed up the data somewhere, or was that your backup disk?

So there are several things you can do here:
If you have another drive you can use **dd** to do a binary dump of all the data onto a file system. However you will then need something else to figure out whas what.

If the entire drive was one partition, you can recreate the partition using gparted via a live cd and not format it. In theory you should be able to get everything back.

Take a look at  the SystemRescueCD at [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

YOu can also check out ddrescue at [http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)

I would suggest doing a data dump so that even if you screw up the recovery you can always have at least the binary dump.

HTH
AM

---

### Post by Sef on 2007-04-17
Also check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

---

