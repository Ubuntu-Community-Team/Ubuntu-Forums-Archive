---
title: "LVM shrink containing partition"
date: 2008-05-08
forum: General Help
---

### Post by qix on 2008-05-08
I have a harddrive formatted with an LVM partition (8e) that is being used as a physical volume for my LVM setup. I've shrunk my LVM partitions and reduced the size of my volume group and physical extent, and now I need the free space to create a normal partition on the disk (so I can create a /boot partition for a new linux install).

My problem is that the partition (type 8e partition) containing the LVM physical extent still seem to fill up the whole disk. How do I reduce the size of that?

Here is some info about the disk:
```
kristian@kristianstat:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   8e  Linux LVM

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00039216

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   8e  Linux LVM

```
```

kristian@kristianstat:~$ sudo pvscan
  PV /dev/sda1   VG kristianvol   lvm2 [298,09 GB / 0    free]
  PV /dev/sdb1   VG kristianvol   lvm2 [281,92 GB / 0    free]
  Total: 2 [580,00 GB] / in use: 2 [580,00 GB] / in no VG: 0 [0   ]
```

```
kristian@kristianstat:~$ sudo pvdisplay /dev/sdb1
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               kristianvol
  PV Size               281,92 GB / not usable 1,69 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              72171
  Free PE               0
  Allocated PE          72171
  PV UUID               LtV7yo-xrUo-vtXq-mj3B-CuxB-n981-nkzDYQ
```

```
kristian@kristianstat:~$ sudo vgdisplay
  --- Volume group ---
  VG Name               kristianvol
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  18
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               580,00 GB
  PE Size               4,00 MB
  Total PE              148481
  Alloc PE / Size       148481 / 580,00 GB
  Free  PE / Size       0 / 0   
  VG UUID               hJL2qh-Wwud-8fMK-CiqV-1S9F-8hCy-iGV2Cn
```

So again, how do I use the free space on sdb??? I need a partition to install Ubuntu on.

---

