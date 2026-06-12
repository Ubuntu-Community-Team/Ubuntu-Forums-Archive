---
title: "Hardware raid expaned - how to expand the lvm?"
date: 2017-07-08
forum: General Help
---

### Post by samcoinc on 2017-07-08
I have a dell server that I just extended a hardware raid volume to 24TB from about 19TB.  I have a lvm that I want to increase and am having a hard time finding a good how to.

This is the physical disk array

```
Disk /dev/sda: 24.6 TiB, 27000311906304 bytes, 52734984192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: E0762F97-C314-4C5A-B176-8C0C1F405522

Device       Start         End     Sectors  Size Type
/dev/sda1     2048        4095        2048    1M BIOS boot
/dev/sda2     4096     1003519      999424  488M Linux filesystem
/dev/sda3  1003520 41016096767 41015093248 19.1T Linux LVM


 --- Physical volume ---
  PV Name               /dev/sda3
  VG Name               artserverz-vg
  PV Size               19.10 TiB / not usable 1.00 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              5006725
  Free PE               168925
  Allocated PE          4837800
  PV UUID               SFMIVj-nau7-c78G-V37g-xkei-h6RS-xsNEXS

  --- Volume group ---
  VG Name               artserverz-vg
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  7
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                3
  Open LV               3
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               19.10 TiB
  PE Size               4.00 MiB
  Total PE              5006725
  Alloc PE / Size       4837800 / 18.45 TiB
  Free  PE / Size       168925 / 659.86 GiB
  VG UUID               m3ejZd-4LrD-lXOM-Rdn5-BqRV-QkeC-Br2NOd
```

what I want to do is expand the volume but cannot because it doesn't see the extra space.  There are references to deleting the partition using fdisk and creating a new one with the correct ending sector.  this scares me a bit.

I did just a 
pvresize /dev/sda3 and id didn't seem to help.

thanks
sam

---

### Post by wildmanne39 on 2017-07-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by samcoinc on 2017-07-08
sorry - 

I think I got it.  I used parted to extend the partition.  Then the lvm saw the extra space and I was able to extend the logical volume.

---

