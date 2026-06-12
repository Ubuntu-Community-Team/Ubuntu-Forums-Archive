---
title: "Hardy doesn't detect my external ext3 hard disk"
date: 2008-04-26
forum: General Help
---

### Post by kinson on 2008-04-26
Hi Guys,

I just recently installed Hardy on my spare hard disk, and after a couple of hiccups, wireless seems to be working using Wicd(yay!).

I noticed one more thing though, is that my external 3.5inch 250GB hard disk isn't detecting. Its formatted as an ext3 drive, and has one big partition.

Nothing seems to show up in gparted, or sudo fdisk -l
```

kinson@kinbuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d4b40e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51200000    7  HPFS/NTFS
/dev/sda2            6376        8806    19527007+  83  Linux
/dev/sda3            8807        8930      996030   82  Linux swap / Solaris
/dev/sda4            8931       24321   123628207+  83  Linux
kinson@kinbuntu:~$ 

```

Funny this is, when I run the sudo fdisk -l command, I can see that the activity light on my external casing flashes red(i.e. activity).

The hard disk is working fine, as I was using it for data backups on my dapper before this. If I did anything out of the norm was that I put it to have a fixed name e.g. "backupdrive" instead of "usbdisk-1" or something like that.

Any help/ideas/suggestions on the matter guys?

Cheers, and thanks in advance !
Kinson

---

