---
title: "Slow bootup and fsck died with exit status 8"
date: 2007-09-01
forum: General Help
---

### Post by 2shanfernando on 2007-09-01
Hi,

I've been chugging along nicely with Feisty but recently I've noticed some strange behaviours, notably that on every second reboot I get:

fsck died with exit status 8

and the bootscreen goes into console mode (instead of the splash) showing me that the system is checking the filesystem for errors.

Here is my fstab:

> 
proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=962a8ced-a159-470d-bcbe-98707bbc5e5d / jfs defaults,errors=remount-ro 0 1
# Entry for /dev/sda8 :
UUID=c53654eb-fd20-4954-a755-080f47c07802 /boot reiserfs notail 0 2
# Entry for /dev/sda9 :
UUID=f32c390b-2325-4dce-934c-da3255a91d17 /home jfs defaults 0 2
# Entry for /dev/sda7 :
UUID=d729ff33-75f1-49b5-bc34-4c11d897e8fc  /opt xfs defaults 0 1

# Entry for /dev/sda5 :
UUID=e1ad96ad-e3a4-4b02-9d2c-245a233d6323 none swap sw 0 2

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
#/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

################################
# Custom Drive Configurations
################################

# Entry for /dev/sdc1 :
UUID=18582b93-31a0-44d1-830f-e35ab0497f5e /media/Storage reiserfs defaults 0 2

UUID=3be19ae9-1296-4753-8d08-f9a2de4b0182 /media/Video  reiserfs defaults 0 2


I am using LVM, with ReiserFS being the filesystem.

fdisk -l
> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   8e  Linux LVM

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   8e  Linux LVM

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   8e  Linux LVM

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   8e  Linux LVM

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   8e  Linux LVM

Disk /dev/sdg: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       30515   245111706    5  Extended
/dev/sdg5               1         131     1052194+  82  Linux swap / Solaris
/dev/sdg6             132        7964    62918541   83  Linux
/dev/sdg7            7965        8616     5237158+  83  Linux
/dev/sdg8            8617        8632      128488+  83  Linux
/dev/sdg9            8633       30515   175775166   83  Linux

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       60801   488384001   8e  Linux LVM


Any ideas? Weird thing is that it fails to load properly (requiring you to press CTRL+D) on the second reboot, once you do press CTRL+D it loads Gnome but when prompted to login it warns you that you cant load a default session (Home partition isnt there).

I've loaded the LiveCD up and done manual fsck's on all the partitions to no avail...

anyone have any ideas?

---

### Post by 2shanfernando on 2007-09-01
Not sure if this is useful but here's whats in the /var/log/messages for this boot:
> 

Sep  1 19:26:31 ZEUS kernel: [   40.779746] bt878: AUDIO driver version 0.0.0 loaded
Sep  1 19:26:31 ZEUS kernel: [   41.322488] Adding 1052184k swap on /dev/disk/by-uuid/e1ad96ad-e3a4-4b02-9d2c-245a233d6323.  Priority:-1 extents:1 across:1052184k
Sep  1 19:26:31 ZEUS kernel: [  232.628686] ReiserFS: dm-11: found reiserfs format "3.6" with standard journal
Sep  1 19:26:31 ZEUS kernel: [  232.628708] ReiserFS: dm-11: using ordered data mode
Sep  1 19:26:31 ZEUS kernel: [  232.632436] ReiserFS: dm-11: journal params: device dm-11, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age
30, max trans age 30
Sep  1 19:26:31 ZEUS kernel: [  232.632834] ReiserFS: dm-11: checking transaction log (dm-11)
Sep  1 19:26:31 ZEUS kernel: [  232.651214] ReiserFS: dm-11: Using r5 hash to sort names
Sep  1 19:26:31 ZEUS kernel: [  232.846918] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
Sep  1 19:26:31 ZEUS kernel: [  232.847175] SGI XFS Quota Management subsystem
Sep  1 19:26:31 ZEUS kernel: [  232.859507] Filesystem "dm-10": Disabling barriers, not supported by the underlying device
Sep  1 19:26:31 ZEUS kernel: [  232.859650] XFS mounting filesystem dm-10
Sep  1 19:26:31 ZEUS kernel: [  232.941699] ReiserFS: dm-0: found reiserfs format "3.6" with standard journal
Sep  1 19:26:31 ZEUS kernel: [  232.941728] ReiserFS: dm-0: using ordered data mode
Sep  1 19:26:31 ZEUS kernel: [  232.945885] ReiserFS: dm-0: journal params: device dm-0, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30
, max trans age 30
Sep  1 19:26:31 ZEUS kernel: [  232.946294] ReiserFS: dm-0: checking transaction log (dm-0)
Sep  1 19:26:31 ZEUS kernel: [  232.999618] ReiserFS: dm-0: Using r5 hash to sort names
Sep  1 19:26:31 ZEUS kernel: [  233.066106] ReiserFS: dm-13: found reiserfs format "3.6" with standard journal
Sep  1 19:26:31 ZEUS kernel: [  233.066161] ReiserFS: dm-13: using ordered data mode
Sep  1 19:26:31 ZEUS kernel: [  233.070515] ReiserFS: dm-13: journal params: device dm-13, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age
30, max trans age 30
Sep  1 19:26:31 ZEUS kernel: [  233.070944] ReiserFS: dm-13: checking transaction log (dm-13)
Sep  1 19:26:31 ZEUS kernel: [  233.084974] ReiserFS: dm-13: Using r5 hash to sort names
Sep  1 19:26:31 ZEUS kernel: [  233.532082] Ethernet Channel Bonding Driver: v3.1.1 (September 26, 2006)


and my UUIDs
> 
lrwxrwxrwx 1 root root 17 2007-09-01 19:22 18582b93-31a0-44d1-830f-e35ab0497f5e -> ../../mapper/sda1
lrwxrwxrwx 1 root root 21 2007-09-01 19:23 3be19ae9-1296-4753-8d08-f9a2de4b0182 -> ../../mapper/vg-Video
lrwxrwxrwx 1 root root 17 2007-09-01 19:22 962a8ced-a159-470d-bcbe-98707bbc5e5d -> ../../mapper/sdg6
lrwxrwxrwx 1 root root 17 2007-09-01 19:22 c53654eb-fd20-4954-a755-080f47c07802 -> ../../mapper/sdg8
lrwxrwxrwx 1 root root 17 2007-09-01 19:22 d729ff33-75f1-49b5-bc34-4c11d897e8fc -> ../../mapper/sdg7
lrwxrwxrwx 1 root root 17 2007-09-01 19:22 e1ad96ad-e3a4-4b02-9d2c-245a233d6323 -> ../../mapper/sdg5
lrwxrwxrwx 1 root root 17 2007-09-01 19:22 f32c390b-2325-4dce-934c-da3255a91d17 -> ../../mapper/sdg9


After all the checks though the filesystems are marked as clean. If I change the fstab to 0 0 instead of 0 2 (which forces a check) this will fail to mount the LVM sometimes.

I havent really rebooted this machine enough to realise this earlier.

thanks for looking.

---

