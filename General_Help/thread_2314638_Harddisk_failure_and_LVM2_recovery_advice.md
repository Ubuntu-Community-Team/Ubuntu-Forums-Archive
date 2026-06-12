---
title: "Harddisk failure and LVM2 recovery advice"
date: 2016-02-22
forum: General Help
---

### Post by zathrusuk on 2016-02-22
Hi 

I have a LVM2 setup with two disks in it both about 500GB, one of these is fine (sda5) and the other has a number of bad sectors and fails smart (sdc1). The system boots just about at the moment, I have purchased a replacement 2TB drive that at the moment has nothing on, can anyone offer any advise the best way to go about recovering data?

I was thinking about using ddrescue to image both disks on to the new 2TB drive, so i could re-create the volume? Is this the right way to go or should I just format the new disk install ubuntu on a partition with the both of the old disk de-powered and then use ddrescue on the logical volumes to copy over the data? If so what would be the correct command?

Thanks in advance

Mike

pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               Main
  PV Size               461.10 GiB / not usable 0
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              118042
  Free PE               0
  Allocated PE          118042
  PV UUID               3zT5DT-2LW5-GAT2-EBUM-OMZc-wJin-qd8QrF

  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               Main
  PV Size               465.76 GiB / not usable 2.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              119234
  Free PE               0
  Allocated PE          119234
  PV UUID               yLfceQ-pcut-Be3z-ZNHA-iuKu-KNjY-Qqrs56

vgdisplay
  --- Volume group ---
  VG Name               Main
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  10
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                5
  Open LV               5
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               926.86 GiB
  PE Size               4.00 MiB
  Total PE              237276
  Alloc PE / Size       237276 / 926.86 GiB
  Free  PE / Size       0 / 0
  VG UUID               5dySiU-yelk-KShY-Ojqn-isy3-K7fa-7Sjnqm

lvdisplay
  --- Logical volume ---
  LV Path                /dev/Main/home
  LV Name                home
  VG Name                Main
  LV UUID                2d1fG8-OhOA-x5y6-qyp7-ugqc-nNQT-335pz1
  LV Write Access        read/write
  LV Creation host, time xxx, 2014-04-20 14:12:13 +0100
  LV Status              available
  # open                 1
  LV Size                46.56 GiB
  Current LE             11920
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0

  --- Logical volume ---
  LV Path                /dev/Main/root
  LV Name                root
  VG Name                Main
  LV UUID                ppFf9i-3Pky-BSW2-UoGg-mQ4u-qiwf-guvzCj
  LV Write Access        read/write
  LV Creation host, time xxx, 2014-04-20 14:12:45 +0100
  LV Status              available
  # open                 1
  LV Size                93.13 GiB
  Current LE             23841
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

  --- Logical volume ---
  LV Path                /dev/Main/User
  LV Name                User
  VG Name                Main
  LV UUID                Rz0g3o-ZXqf-JIB4-l22o-jw9A-r9LK-mTCuu6
  LV Write Access        read/write
  LV Creation host, time xxxx, 2014-04-20 14:13:30 +0100
  LV Status              available
  # open                 1
  LV Size                46.56 GiB
  Current LE             11920
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2

  --- Logical volume ---
  LV Path                /dev/Main/swap
  LV Name                swap
  VG Name                Main
  LV UUID                zTNxRb-SZkr-F4oV-TBNS-7lES-mtp1-JrsEsP
  LV Write Access        read/write
  LV Creation host, time xxx, 2014-04-20 14:14:27 +0100
  LV Status              available
  # open                 2
  LV Size                9.31 GiB
  Current LE             2384
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3

  --- Logical volume ---
  LV Path                /dev/Main/share
  LV Name                share
  VG Name                Main
  LV UUID                0rPWdC-RfsV-6wEs-BWFB-4OH8-cR07-8nMbFa
  LV Write Access        read/write
  LV Creation host, time xx, 2014-04-20 14:14:31 +0100
  LV Status              available
  # open                 1
  LV Size                731.29 GiB
  Current LE             187211
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:4

---

