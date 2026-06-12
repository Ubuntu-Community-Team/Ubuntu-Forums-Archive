---
title: "Need help with existing RAID1 array..."
date: 2008-04-27
forum: General Help
---

### Post by Aceninja on 2008-04-27
Hi,

After giving Windows the boot, I have installed the latest version of Ubuntu (Hardy Heron) onto my system. It took me a while to get the NTFS partitions to work, but the main issue is this:

I've got two 250gig SATA hdd's configured as RAID1 in BIOS using Intel's ICH7r (Soft/Fake-raid)

It worked fine in windows, but Ubuntu sees them as two separate disks

I've heard mdadm can do the trick, but I am trying to setup an already existing/previously existed (depending on how u look at it) RAID array. I don't want to format anything and lose data. How can I get this to work?

Any suggestions would be highly appreciated. Total newbie here...

ps: here is my fdisk -l output

> 
Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06310630

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4501    36149248    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbac8d757

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbac8d757

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sde: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ae84ae8

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       17495   140528556   83  Linux
/dev/sde2           17496       18241     5992245    5  Extended
/dev/sde5           17496       18241     5992213+  82  Linux swap / Solaris

Disk /dev/sdf: 1021 MB, 1021312512 bytes
129 heads, 16 sectors/track, 966 cylinders
Units = cylinders of 2064 * 512 = 1056768 bytes
Disk identifier: 0xae6a1b47

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         967      997367+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(972, 128, 16) logical=(966, 57, 15)

 

The raid disks are SDD1 and SDC1.

Can someone please walk me through this?

---

