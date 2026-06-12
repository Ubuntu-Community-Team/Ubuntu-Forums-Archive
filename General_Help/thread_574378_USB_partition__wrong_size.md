---
title: "USB partition / wrong size"
date: 2007-10-12
forum: General Help
---

### Post by mattbatt77 on 2007-10-12
USB = sanDisk titanium cruzer, 512MB, no U3 software.

I have had this device 3 years, formatted FAT32 which would run between my mac and PC. It started not being recognized on my mac one day, so I said reformat, and at that time, disk manager nor terminal in OSX could format it (it would say error).

So I tried on XP (FAT 16, 32, quick format, using disk manager). Won't reformat, says it can't.

At this point, I also noticed that the disk is showing up as a 249 MB device in disk manager (and I can't delete the partition, it is grayed out).

Gnome partitioner won't work.

I started the PC on Ubuntu Live CD, and this is what I've done so far: 

> Disk /dev/sdc: 259 MB, 259522560 bytes
8 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 496 * 512 = 253952 bytes

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-1021, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-1021, default 1021): 
Using default value 1021

Command (m for help): p

Disk /dev/sdc: 259 MB, 259522560 bytes
8 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 496 * 512 = 253952 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1021      253177   83  Linux

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 6
Changed system type of partition 1 to 6 (FAT16)

Command (m for help): p

Disk /dev/sdc: 259 MB, 259522560 bytes
8 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 496 * 512 = 253952 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1021      253177    6  FAT16

Command (m for help): w
The partition table has been altered!
e

Cool, but it isn't 512 MB.

So I tried this:
> root@ubuntu:/home/ubuntu# resize2fs /dev/sdc
resize2fs 1.40-WIP (14-Nov-2006)
resize2fs: Bad magic number in super-block while trying to open /dev/sdc
Couldn't find valid filesystem superblock.


It seems to me that there is a bad partition table only allowing the computer to see 249 MB. How can I fix this and reformat?

---

