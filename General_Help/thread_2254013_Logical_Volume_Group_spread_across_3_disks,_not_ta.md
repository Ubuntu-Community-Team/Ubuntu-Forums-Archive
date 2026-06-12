---
title: "Logical Volume Group spread across 3 disks, not taking up full space?"
date: 2014-11-24
forum: General Help
---

### Post by Dave_Grant on 2014-11-24
Hi, totally new to Ubuntu but successfully installed and created a Volume Group and Logical Volume which spans 3 HDDs (1x1TB, 2xTB). My problem is that the logical volume doesn't seem to take up all the available space (5TB).

vgdisplay lists the volume group vg_media as 4.55TiB with Alloc PE / Size as 3.91TiB and Free PE / Size as 657.54GiB

lvdisplay lists LV Size as 3.91TiB

Desktop labels the volume as 4.3TiB

How can I get this to consume the full available space, 5TiB?

I've pasted full output for vgdisplay, lvdisplay and fdisk -l below. Please let me know if any other information would be helpful.

Thanks

```
htpc@htpc-desktop:~$ sudo vgdisplay
[sudo] password for htpc: 
  --- Volume group ---
  VG Name               vg_media
  System ID             
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  11
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               4.55 TiB
  PE Size               4.00 MiB
  Total PE              1192329
  Alloc PE / Size       1024000 / 3.91 TiB
  Free  PE / Size       168329 / 657.54 GiB
  VG UUID               OIwNRH-MQFT-cJO0-zJ7s-Px80-zdnl-pofJ1r
   
htpc@htpc-desktop:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg_media/lv_media
  LV Name                lv_media
  VG Name                vg_media
  LV UUID                gwup3W-zAV7-tnZz-pNlP-JTrx-vQoE-lzOD3G
  LV Write Access        read/write
  LV Creation host, time htpc-desktop, 2014-11-23 23:17:00 +0000
  LV Status              available
  # open                 1
  LV Size                3.91 TiB
  Current LE             1024000
  Segments               3
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
htpc@htpc-desktop:~$ sudo fdisk -l

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef883

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   109418495    54708224   83  Linux
/dev/sda2       109420542   125044735     7812097    5  Extended
/dev/sda5       109420544   125044735     7812096   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x001378d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907029167  1953513560   8e  Linux LVM

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x78f40842

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  1953521663   976759808   83  Linux

Disk /dev/mapper/vg_media-lv_media: 4295.0 GB, 4294967296000 bytes
255 heads, 63 sectors/track, 522166 cylinders, total 8388608000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_media-lv_media doesn't contain a valid partition table


```

---

### Post by Impavidus on 2014-11-24
5TB=5/1.024^4=4.55TiB. Makes perfect sense. That's the difference between terabytes and terabinarybytes.

---

### Post by Dave_Grant on 2014-11-24
Thanks. I've extended it out and it's listing as 5.0TB in desktop now.

---

