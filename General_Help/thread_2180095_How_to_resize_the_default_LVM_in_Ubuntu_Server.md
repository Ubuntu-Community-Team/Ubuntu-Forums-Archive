---
title: "How to resize the default LVM in Ubuntu Server?"
date: 2013-10-11
forum: General Help
---

### Post by Noobstar on 2013-10-11
The system is a virtual machine with default installation of Ubuntu Server. I have a bit of experience with Ubuntu Server, but not with LVM. Here's the situation:

```
$ *sudo pvscan*
  PV /dev/sda5   VG ubuntu1204lts-vg   lvm2 [119.76 GiB / 0    free]
  Total: 1 [119.76 GiB] / in use: 1 [119.76 GiB] / in no VG: 0 [0   ]
$ *sudo pvdisplay*
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               ubuntu1204lts-vg
  PV Size               119.76 GiB / not usable 2.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              30658
  Free PE               0
  Allocated PE          30658
  PV UUID               fPv0q3-ARfR-sqQy-jrf9-8sj1-JdPL-enwbUa
```

What I would like to do, is split the above into one 80 GB EXT4 partition with the system, and one partition of about 40 GB which I can format with case-insensitive JFS. I have tried googling, but couldn't find anything which seemed applicable.
Also, I should mention that I do not have physical access and can not boot off any removable medium.

I *could* repartition and reinstall the entire machine without LVM, but LVM seems a nifty concept - if only I could get the hang of it!

---

### Post by L486XGW on 2013-10-11
What do you get with the following commands:

vgdisplay

lvdisplay

df -h

---

### Post by Noobstar on 2013-10-11
> **L486XGW said:**
> What do you get with the following commands:

vgdisplay

lvdisplay

df -h

```
*$ sudo vgdisplay*
  --- Volume group ---
  VG Name               ubuntu1204lts-vg
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               119.76 GiB
  PE Size               4.00 MiB
  Total PE              30658
  Alloc PE / Size       30658 / 119.76 GiB
  Free  PE / Size       0 / 0
  VG UUID               UhIrld-77NY-7FuQ-ptKq-Gm6k-L9UC-wGHtRR

*$ sudo lvdisplay*
  --- Logical volume ---
  LV Name                /dev/ubuntu1204lts-vg/root
  VG Name                ubuntu1204lts-vg
  LV UUID                HNx4Ep-vni5-f2X4-52qF-vqEp-iC2A-qEPitm
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                115.76 GiB
  Current LE             29634
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0

  --- Logical volume ---
  LV Name                /dev/ubuntu1204lts-vg/swap_1
  VG Name                ubuntu1204lts-vg
  LV UUID                MNkasg-5gol-yIUq-d3vt-twpJ-9qgp-7uhfaP
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                4.00 GiB
  Current LE             1024
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

*$ sudo df -h*
Filesystem                          Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu1204lts--vg-root  114G   76G   34G  70% /
udev                                2.0G  4.0K  2.0G   1% /dev
tmpfs                               790M  312K  790M   1% /run
none                                5.0M     0  5.0M   0% /run/lock
none                                2.0G     0  2.0G   0% /run/shm
/dev/sda1                           228M   53M  164M  25% /boot
```

---

### Post by Noobstar on 2013-10-14
Google suggests resizing the system can't be done except by booting from an external medium (e.g. a live cd) and even then it's a complex and risky operation. I'll reformat and reinstall without LVM.

---

