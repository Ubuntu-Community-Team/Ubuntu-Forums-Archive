---
title: "How to change mount name of logical volume group"
date: 2014-11-24
forum: General Help
---

### Post by Dave_Grant on 2014-11-24
[COLOR=#000000][FONT=verdana]I've created a volume group called vg_media and a logical volume within that called lv_media which includes 3 physical disks, 2x2TB and 1xTB.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Once mounted, ubuntu desktop lists the volume in the sidebar as "5.0 TB Volume" however selecting properties for the mount lists "a2417239-7499-47e0-8bb6-c71695740544" as the name and will not allow me to rename under the basic tab as the "Device or resource busy".[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]This has recently changed by appending a '1' to the above name and has messed up some application-specific relative paths so i'm wondering, what is this name? can i rename this to be something more semantic? and finally, how do i mount this volume on autostart?[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]New to LVM so not sure i've set this up right, any advice is much appreciated. Thanks. (basically trying to combine 3+disks into single addressable volume which mounts on boot with a static path/name).
[/FONT][/COLOR]
[HR][/HR][COLOR=#000000][FONT=verdana][URL="https://i.imgur.com/Sbhvf0i.png"]
Screenshot of new mount name, error message.[/URL]
[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana][B]fdisk -l :

[/B][/FONT][/COLOR]```

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

Disk /dev/mapper/vg_media-lv_media: 4990.8 GB, 4990751997952 bytes
255 heads, 63 sectors/track, 606757 cylinders, total 9747562496 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_media-lv_media doesn't contain a valid partition table

```

[COLOR=#000000][FONT=verdana][B]vgdisplay :
[/B][/FONT][/COLOR]
```

htpc@htpc-desktop:~$ sudo vgdisplay
  --- Volume group ---
  VG Name               vg_media
  System ID             
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  15
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
  Alloc PE / Size       1189888 / 4.54 TiB
  Free  PE / Size       2441 / 9.54 GiB
  VG UUID               OIwNRH-MQFT-cJO0-zJ7s-Px80-zdnl-pofJ1r

```

[COLOR=#000000][FONT=verdana][B]lvdisplay :

[/B][/FONT][/COLOR]```

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
  LV Size                4.54 TiB
  Current LE             1189888
  Segments               3
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0

```

---

