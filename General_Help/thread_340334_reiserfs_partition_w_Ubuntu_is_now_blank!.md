---
title: "reiserfs partition /w Ubuntu is now blank!?"
date: 2007-01-17
forum: General Help
---

### Post by reakin on 2007-01-17
I think I just lost a project that I have been working on for over a year, and now all the sudden I cannot find any backups... I'm doomed unless someone can help.

I recently installed a dualboot system running Ubuntu Edgy on ReiserFS and Windows XP.  Everything was working fine for a while, I could boot into either OS using Grub.  Then, out of nowhere Grub was skipped and Windows booted up.  I used the Ubuntu Desktop CD to run Ubuntu and mount the ReiserFS partition, only to find it blank!  I don't know what to do, but of course there are indispensable files on that partition.  

Suggestions are eagerly awaited, thanks for any you have.

Rich

---

### Post by randomnumber on 2007-01-17
I doubt it was deleted. I think that it is just not mounted and when you open a folder that isn't mounted to you get a blank folder. 

what folder do you open to access the drive: example: /media/thispartition

reply back the output of "mount" in a terminal

if there is not a link listed to your folder then it is not mounted.

---

### Post by randomnumber on 2007-01-17
more information that would be useful: sudo fdisk -l

---

### Post by reakin on 2007-01-17
Thanks for looking,

fdisk -l looks like this:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       14593    86501992+   f  W95 Ext'd (LBA)
/dev/sda5            3825        7648    30716248+  83  Linux
/dev/sda6            7649       14468    54781618+   b  W95 FAT32
/dev/sda7           14469       14593     1004031   82  Linux swap / Solaris


/dev/sda5 is the partition that has Ubuntu (or had) installed on it.

this is how I mount it in /mnt/blarg:

ubuntu@ubuntu:~$sudo mount -v -t reiserfs /dev/sda5 /mnt/blarg/
/dev/sda5 on /mnt/blarg type reiserfs (rw)

And alas, /mnt/blarg is empty.  I cannot tell how or why.

---

