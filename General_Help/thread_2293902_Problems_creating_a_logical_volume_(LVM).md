---
title: "Problems creating a logical volume (LVM)"
date: 2015-09-08
forum: General Help
---

### Post by haraldweber2 on 2015-09-08
I'm trying to create an additional logical volume after i have expanded the partition and resized the physical lvm volume.
The error message is: **Insufficient free space: 786432 extents needed, but only 0 available**

I want to create a 3TB volume. The volume group has 5.4T free.
The command **pvdisplay **says that I have **1417100 free extents available**. 

What can be the Problem?

```
$ pvssudo lvcreate -L 3T lvm -n data  PV                     VG   Fmt  Attr PSize PFree
  /dev/mapper/sda2_crypt lvm  lvm2 ---  5.46t 5.41t


$ vgs
  VG   #PV #LV #SN Attr   VSize VFree
  lvm    1   2   0 wz--n- 5.46t 5.41t
  
$ lvs
  LV     VG   Attr      LSize  Pool Origin Data%  Move Log Copy%  Convert
  rootfs lvm  -wi-ao--- 29.80g
  swap   lvm  -wi-ao--- 22.35g


$ lvcreate -L 3T lvm -n data
  Insufficient free space: 786432 extents needed, but only 0 available

```

```
$ pvdisplay  --- Physical volume ---
  PV Name               /dev/mapper/sda2_crypt
  VG Name               lvm
  PV Size               5.46 TiB / not usable 3.98 MiB
  Allocatable           NO
  PE Size               4.00 MiB
  Total PE              1430451
  Free PE               1417100
  Allocated PE          13351
  PV UUID               ezMl1N-NcWo-nBFQ-v147-8q0J-VBPz-Lh0SMx



```

---

### Post by TheFu on 2015-09-08
PV Size               5.46 TiB / not usable 3.98 MiB

???? Why is that?

---

### Post by haraldweber2 on 2015-09-09
I did the process a second time and now it works... Something was weird i think.
Resize partition -> resize luks volume -> resize pv

---

