---
title: "Auto mount NTFS at boot"
date: 2016-06-07
forum: General Help
---

### Post by richyrichuk2 on 2016-06-07
Hi, i am struggling to auto mount at startup 4 drives. managed to resolve samba shares, but not without having to manually click to mount the drives. the GUI in disks simply doesnt work. i did read about the reported bug for "show in user interface" and that PySDM hasn't been updated in a long time. i have been unable to understand the fdisk commands so far. simply looking to auto mount the drives at startup. help would be apprichated.


```
Disk /dev/sda: 250.1 GB, 250059350016 bytes255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00021df7


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   486563839   243280896   83  Linux
/dev/sda2       486565886   488396799      915457    5  Extended
/dev/sda5       486565888   488396799      915456   82  Linux swap / Solaris


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d


This doesn't look like a partition table
Probably you selected the wrong device.


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     6579571  1924427647   958924038+  70  DiskSecure Multi-Boot
/dev/sdb2   ?  1953251627  3771827541   909287957+  43  Unknown
/dev/sdb3   ?   225735265   225735274           5   72  Unknown
/dev/sdb4      2642411520  2642463409       25945    0  Empty


Partition table entries are not in disk order


Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79db79db


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  2930272064  1465136001    7  HPFS/NTFS/exFAT


Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41413535


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  2930272064  1465136001    7  HPFS/NTFS/exFAT


Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ae085


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1250263727   625130840    7  HPFS/NTFS/exFAT




```

ubuntu 14.04
all NTFS drives
mount the drive not a folder


thanks

Rich

---

### Post by decrepit on 2016-06-07
You need to enter them in /etc/fstab, I don't have the exact details in my head, but searching how to do it should come up with something helpfull

---

### Post by decrepit on 2016-06-07
Another thought, ```
 man fstab 
``` will tell you what to do.

---

### Post by yetimon_64 on 2016-06-07
Here is a wiki guide for mounting ntfs partitions via an /etc/fstab entry : [https://help.ubuntu.com/community/MountingWindowsPartitions#NTFS](https://help.ubuntu.com/community/MountingWindowsPartitions#NTFS)

As decrepit notes an fstab entry is the way to do it. This guide shows how to get UUIDs for identification. I would advise you use UUIDs and not device numbering as some online guides show (eg. /dev/sdb# etc). Device numbers can on occasion change, UUIDs have far less chance of ever changing.

Where the guide shows to use the command "sudo blkid" I always tend to use "sudo blkid -c /dev/null" the extra switch for cache to use /dev/null forces the command to poll the actual hardware and not rely on any cached values. The rest of the wiki guide looks like what you will need. Good luck, yeti.

---

### Post by Morbius1 on 2016-06-07
In order for anyone to help you with this they will need more information. Posting the output of these commands should do that:
```
cat /etc/fstab
```
```
sudo blkid -c /dev/null -o list
```

---

### Post by richyrichuk2 on 2016-06-07
thanks for reply decrepit. i looked at fstab but couldnt get the exact details down i needed.

ahh yes ok i will used UUID then if hats more stable yetimon_64. thanks.

ok so here's the spit out from the commands morbius1

i THINK it's in working order but again after a lot of tweeking they seem to auto mount at startup. like i said it seems to be working. did a cold boot and all remounted fine just unsure of stability of this or even if that should be a concern.

```
[B]cat /etc/fstab
[/B]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=56c7c2ba-b850-4c2c-bf97-b8457e72aedf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=60e80d2a-5685-47e0-b538-21e3d8cd8678 none            swap    sw              0       0
/dev/sdb /mnt/sdb auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/sde1 /mnt/sde1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/sdc1 /mnt/sdc1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/sdd1 /mnt/sdd1 auto nosuid,nodev,nofail,x-gvfs-show 0 0




**sudo blkid -c /dev/null -o list**


device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              56c7c2ba-b850-4c2c-bf97-b8457e72aedf
/dev/sda5  swap             <swap>         60e80d2a-5685-47e0-b538-21e3d8cd8678
/dev/sdb   ntfs    1        /mnt/sdb       78E6111E71C1F9CF
/dev/sdc1  ntfs    2        /mnt/sdc1      1D7862AD236FA13E
/dev/sdd1  ntfs    3        /mnt/sdd1      FA9AB9FA9AB9B38B
/dev/sde1  ntfs    4        /mnt/sde1      2EA8A8F8A8A8C027
```

---

### Post by Morbius1 on 2016-06-08
The issue here and the one yetimon_64 posted about is the use of /dev/sdxy to designate the partitions in fstab. sdxy is a relative term. Based on Lunar cycles, humidity, and sun spot activity what the system sees as sdc on one boot it may very well see as sdd on another. That's why UUID's were invented since they don't change.

So this for example:
 > /dev/sdd1 /mnt/sdd1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
Would look like this:
 > [COLOR=#0000cd]UUID=FA9AB9FA9AB9B38B[/COLOR] /mnt/sdd1 auto nosuid,nodev,nofail,x-gvfs-show 0 0

* This is a rather curious thing though isn't it:*
> /dev/sdb /mnt/sdb auto nosuid,nodev,nofail,x-gvfs-show 0 0
If we look at something like /dev/sdc1 as an example, sdc is a physical device - the hard drive itself. sdc1 is a partition on that hard drive. You don't mount hard drives you mount partitions on hard drives even if there is only one partition on that hard drive. I don't quite know what to make of /dev/sdb. That's a hard drive not a partition yet is shows up as one. That cannot be. There’s probably a logical reason for that I just don't know what it is.

---

### Post by oldfred on 2016-06-08
To reinforce the issue of device like /dev/sdb1 instead of UUID as posted above.

My old BIOS system, I built myself. But did not pay attention to order drives were plugged into SATA ports. And it did not matter much until multiple drives & then I started using flash drives.
I plugged in flash drive and it was sde, but on reboot it became sdb and every drive after that moved one letter. I had skipped SATA port 1.

You would think I learned my lesson, but new UEFI system, I had first drive (hd0) in SATA0, DVD in SATA1 and second drive in SATA2.
While second drive was sdb, in grub it was hd2, not hd1. 

Or always use SATA ports in order on motherboard and use UUIDs, so drive order then is not critical.

---

### Post by kurt18947 on 2016-06-08
I found a utility in the Ubuntu repositories for managing the mounting of NTFS drives. I don't have access to that machine so can't tell you the name - I suspect it was ntfs-config though the description in synaptic says it helps configure ntfs write.

---

### Post by oldfred on 2016-06-08
Last I heard was that NTFS Config not updated to use UUID's.
Disks may also set mounts, but you have to know correct parameters and its defaults are not optimal.

       [URL="https://help.ubuntu.com/community/MountingWindowsPartitions"]https://help.ubuntu.com/community/MountingWindowsPartitions
[/URL]       
 Morbius1 may have newer settings than what was here. When I last use NTFS I used this as my example to copy & paste into fstab.
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)

---

