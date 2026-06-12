---
title: "LVM cannot find device"
date: 2014-11-30
forum: General Help
---

### Post by kaar3l on 2014-11-30
Hello, I pulled out of my nas (Synology) disk, to recover a deleted folder.
I got the /dev/md2 and /dev/md3 devices in raid0 started.

cat /proc/mdstat
```
md3 : active raid1 sda6[1]
      976742784 blocks super 1.2 [2/1] [_U]
      
md2 : active raid1 sdb5[2]
      1948779648 blocks super 1.2 [2/1] [_U]
      
unused devices: <none>
```
So now I have two /dev/md2 and /dev/md3 that need to be in LVM. 
So I did pvscan
```
Couldn't find device with uuid 8s9LfU-Egt2-sbtJ-1zkH-ewqb-LjRT-xZ2RC2.
  PV unknown device   VG vg1000   lvm2 [1.81 TiB / 0    free]
  PV /dev/md3         VG vg1000   lvm2 [931.49 GiB / 0    free]
  Total: 2 [2.72 TiB] / in use: 2 [2.72 TiB] / in no VG: 0 [0   ]

```
And it just cannot find the device with that uuid, but its right there:
blkid:
```
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="bb4b1f59-9349-4e59-cced-5de7ca715931" TYPE="linux_raid_member" 
/dev/sdb2: UUID="291dec99-01d5-7031-cced-5de7ca715931" TYPE="linux_raid_member" 
/dev/sdb5: UUID="46288321-39d3-353d-7014-c3a9333d1c33" UUID_SUB="f4d9a1ad-19b5-78b8-c9df-067e8171c7e8" LABEL="DiskStation:2" TYPE="linux_raid_member" 
/dev/sdb6: UUID="a7ff03a3-29c2-a100-ecdd-c31c151ca783" UUID_SUB="33b23fee-5dad-73dc-0f0d-e8ac602cfe33" LABEL="NAS:3" TYPE="linux_raid_member" 
/dev/sda1: UUID="bb4b1f59-9349-4e59-cced-5de7ca715931" TYPE="linux_raid_member" 
/dev/sda2: UUID="291dec99-01d5-7031-cced-5de7ca715931" TYPE="linux_raid_member" 
/dev/sda5: UUID="46288321-39d3-353d-7014-c3a9333d1c33" UUID_SUB="48fd71d6-2182-6dc3-8ae2-796be8eaa383" LABEL="DiskStation:2" TYPE="linux_raid_member" 
/dev/sda6: UUID="a7ff03a3-29c2-a100-ecdd-c31c151ca783" UUID_SUB="135ce55f-a324-5cc5-50b7-106279909111" LABEL="NAS:3" TYPE="linux_raid_member" 
/dev/sdc1: UUID="09d3c590-3a6a-4436-8718-7c14ab0e282b" TYPE="ext4" 
/dev/sdd1: LABEL="USB" UUID="4A54-4A67" TYPE="vfat" 
/dev/md2: UUID="8s9LfU-Egt2-sbtJ-1zkH-ewqb-LjRT-xZ2RC2" TYPE="LVM2_member" 
/dev/md2p1: LABEL="1.42.6-4493" UUID="8da77aa4-43ff-4cd1-81f0-f311284e0b04" TYPE="ext4" 
/dev/md3: UUID="Eu0fsK-Cu1W-3PCw-ZEV6-80fL-05rf-H0qlcE" TYPE="LVM2_member" 

```
It worked in synology box.

fdisk -l
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000c6404

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907028991  1953513472   83  Linux

Disk /dev/sdd: 8086 MB, 8086609920 bytes
4 heads, 44 sectors/track, 89739 cylinders, total 15794160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022203

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048    15792127     7895040    b  W95 FAT32

Disk /dev/md2: 1995.6 GB, 1995550359552 bytes
2 heads, 4 sectors/track, 487194912 cylinders, total 3897559296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

    Device Boot      Start         End      Blocks   Id  System
/dev/md2p1   *        1152  3897558143  1948778496   83  Linux

Disk /dev/md3: 1000.2 GB, 1000184610816 bytes
2 heads, 4 sectors/track, 244185696 cylinders, total 1953485568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md3 doesn't contain a valid partition table

```
So fdisk -l shows kinda akward /dev/md2p1, maybe thats the problem. How could I get the LVM working in ubuntu that I could use extundelete?

---

