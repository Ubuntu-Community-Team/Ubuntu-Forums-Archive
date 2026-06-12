---
title: "Issue with Raid 10 superblock failing"
date: 2012-11-16
forum: General Help
---

### Post by mordred99 on 2012-11-16
Okay .. I am a wits end with this. I have been running 12.04 for the last 5 months in a raid 10 configuration (4-1TB disks). Everything was fine until I reboted yesterday and I got a "failed superblock" error message. The disks are there, but I cannot boot and I cannot get anything to work. I have spent about 10 hours trying to get things back up and running by trying to recreate the superblock, but that does not work. I am now booting off a thumb drive and I need to get this data back.

I usually can create the array in a pen drive install of mint and mount the drive by doing the following:

mdadm --create /dev/md0 --level=10 --raid-devices=4 /dev/sd[abde]1 ..... (The pen drive is C for some reason)

When I do that I get:

mint mnt # mdadm --create /dev/md0 --level=10 --raid-devices=4 /dev/sd[abde]1
mdadm: /dev/sda1 appears to contain an ext2fs file system
size=976760832K mtime=Thu Jan 1 00:00:00 1970
mdadm: /dev/sda1 appears to be part of a raid array:
level=raid10 devices=4 ctime=Thu Nov 15 16:08:02 2012
mdadm: /dev/sdb1 appears to contain an ext2fs file system
size=976237568K mtime=Thu Jan 1 00:00:00 1970
mdadm: /dev/sdb1 appears to be part of a raid array:
level=raid10 devices=4 ctime=Thu Nov 15 16:08:02 2012
mdadm: /dev/sdd1 appears to contain an ext2fs file system
size=976237568K mtime=Thu Jan 1 00:00:00 1970
mdadm: /dev/sdd1 appears to be part of a raid array:
level=raid10 devices=4 ctime=Thu Nov 15 16:08:02 2012
mdadm: /dev/sde1 appears to contain an ext2fs file system
size=976237568K mtime=Thu Jan 1 00:00:00 1970
mdadm: /dev/sde1 appears to be part of a raid array:
level=raid10 devices=4 ctime=Thu Nov 15 16:08:02 2012


After that I am able to sucessfully start it, but then I try to mount it with:

mount -t ext4 /dev/md0 /mnt/temp

And I get an error talking about the superblock and not a valid ext4 file system.


Any help would be appreciated. Below are commands that I can think to run. This is all my lifes work, and my backup failed (thus the reboot to start with). I really cannot loose it all, so please let me know if you have any suggestions.

mint mnt # more /proc/mdstat
Personalities : [raid10]
md0 : active raid10 sde1[3] sdd1[2] sdb1[1] sda1[0]
1952211968 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]

unused devices: <none>


mint mnt # fdisk -l /dev/sda

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a45d1

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 1953523711 976760832 83 Linux


mint mnt # fdisk -l /dev/sdb

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003eab0

Device Boot Start End Blocks Id System
/dev/sdb1 * 2048 1952477183 976237568 83 Linux


mint mnt # fdisk -l /dev/sdd

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061a48

Device Boot Start End Blocks Id System
/dev/sdd1 * 2048 1953523711 976760832 83 Linux


mint mnt # fdisk -l /dev/sde

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000194d8

Device Boot Start End Blocks Id System
/dev/sde1 * 2048 1952477183 976237568 83 Linux






mint mnt # mdadm --examine /dev/sda1
/dev/sda1:
Magic : a92b4efc
Version : 1.2
Feature Map : 0x0
Array UUID : db9e3115:556a49db:27c42d30:02657472
Name : mint:0 (local to host mint)
Creation Time : Thu Nov 15 16:08:02 2012
Raid Level : raid10
Raid Devices : 4

Avail Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
Array Size : 1952211968 (1861.77 GiB 1999.07 GB)
Used Dev Size : 1952211968 (930.89 GiB 999.53 GB)
Data Offset : 262144 sectors
Super Offset : 8 sectors
State : clean
Device UUID : 933ec5c0:d6819e33:adb0e6c8:90e337bd

Update Time : Thu Nov 15 20:08:55 2012
Checksum : b516984f - correct
Events : 17

Layout : near=2
Chunk Size : 512K

Device Role : Active device 0
Array State : AAAA ('A' == active, '.' == missing)
mint mnt # mdadm --examine /dev/sdb1
/dev/sdb1:
Magic : a92b4efc
Version : 1.2
Feature Map : 0x0
Array UUID : db9e3115:556a49db:27c42d30:02657472
Name : mint:0 (local to host mint)
Creation Time : Thu Nov 15 16:08:02 2012
Raid Level : raid10
Raid Devices : 4

Avail Dev Size : 1952212992 (930.89 GiB 999.53 GB)
Array Size : 1952211968 (1861.77 GiB 1999.07 GB)
Used Dev Size : 1952211968 (930.89 GiB 999.53 GB)
Data Offset : 262144 sectors
Super Offset : 8 sectors
State : clean
Device UUID : 9d6df7c7:ce401405:4ea18763:a528ecc5

Update Time : Thu Nov 15 20:08:55 2012
Checksum : 3103c408 - correct
Events : 17

Layout : near=2
Chunk Size : 512K

Device Role : Active device 1
Array State : AAAA ('A' == active, '.' == missing)
mint mnt # mdadm --examine /dev/sdd1
/dev/sdd1:
Magic : a92b4efc
Version : 1.2
Feature Map : 0x0
Array UUID : db9e3115:556a49db:27c42d30:02657472
Name : mint:0 (local to host mint)
Creation Time : Thu Nov 15 16:08:02 2012
Raid Level : raid10
Raid Devices : 4

Avail Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
Array Size : 1952211968 (1861.77 GiB 1999.07 GB)
Used Dev Size : 1952211968 (930.89 GiB 999.53 GB)
Data Offset : 262144 sectors
Super Offset : 8 sectors
State : clean
Device UUID : fa1a1b82:989e933a:95e4d249:5cee901d

Update Time : Thu Nov 15 20:08:55 2012
Checksum : 5ea6d02d - correct
Events : 17

Layout : near=2
Chunk Size : 512K

Device Role : Active device 2
Array State : AAAA ('A' == active, '.' == missing)
mint mnt # mdadm --examine /dev/sde1
/dev/sde1:
Magic : a92b4efc
Version : 1.2
Feature Map : 0x0
Array UUID : db9e3115:556a49db:27c42d30:02657472
Name : mint:0 (local to host mint)
Creation Time : Thu Nov 15 16:08:02 2012
Raid Level : raid10
Raid Devices : 4

Avail Dev Size : 1952212992 (930.89 GiB 999.53 GB)
Array Size : 1952211968 (1861.77 GiB 1999.07 GB)
Used Dev Size : 1952211968 (930.89 GiB 999.53 GB)
Data Offset : 262144 sectors
Super Offset : 8 sectors
State : clean
Device UUID : 594ed481:471ef11a:027f1c24:6f9d057d

Update Time : Thu Nov 15 20:08:55 2012
Checksum : 786bd4bc - correct
Events : 17

Layout : near=2
Chunk Size : 512K

Device Role : Active device 3
Array State : AAAA ('A' == active, '.' == missing)

---

