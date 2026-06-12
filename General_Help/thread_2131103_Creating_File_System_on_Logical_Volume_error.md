---
title: "Creating File System on Logical Volume error"
date: 2013-03-31
forum: General Help
---

### Post by molnar20 on 2013-03-31
Here is the command I'm using and the error I'm getting
```
Executing command partprobe ; mkfs -t ext4 -q /dev/CollinServer/VirturalBoxVMs ..
 

Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1 has been opened read-only. Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1 has been opened read-only. Error: The partition's data region doesn't occupy the entire partition.  .. command complete.
```

Here's my PVs
```
sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               CollinServer
  PV Size               148.81 GiB / not usable 2.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              38095
  Free PE               19380
  Allocated PE          18715
  PV UUID               wNWsYX-0Jx3-DjEB-nASp-FKbR-y0Be-bz137X
   
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               CollinServer
  PV Size               595.52 GiB / not usable 1.97 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              152452
  Free PE               0
  Allocated PE          152452
  PV UUID               aMeTU0-pNK3-GGJb-WrnG-qiCz-6XWU-12p3SM
   


```


and my LVs

```
  --- Logical volume ---
  LV Path                /dev/CollinServer/root
  LV Name                root
  VG Name                CollinServer
  LV UUID                TZFfyh-U97j-EyGC-jYWD-nHFO-YrLa-vnFpD4
  LV Write Access        read/write
  LV Creation host, time CollinServer, 2013-03-31 13:44:35 -0400
  LV Status              available
  # open                 1
  LV Size                16.69 GiB
  Current LE             4272
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/CollinServer/swap_1
  LV Name                swap_1
  VG Name                CollinServer
  LV UUID                vO16ZR-MQYi-fW12-JJj5-kbqJ-9bTC-1pizXI
  LV Write Access        read/write
  LV Creation host, time CollinServer, 2013-03-31 13:44:36 -0400
  LV Status              available
  # open                 2
  LV Size                1.93 GiB
  Current LE             495
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Path                /dev/CollinServer/VirturalBoxVMs
  LV Name                VirturalBoxVMs
  VG Name                CollinServer
  LV UUID                kKU7oj-LieD-AszR-6Aoq-5GV2-Mexo-loVuC7
  LV Write Access        read/write
  LV Creation host, time CollinServer, 2013-03-31 15:59:12 -0400
  LV Status              available
  # open                 0
  LV Size                50.00 GiB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   
  --- Logical volume ---
  LV Path                /dev/CollinServer/MediaShare
  LV Name                MediaShare
  VG Name                CollinServer
  LV UUID                sTM9Nh-yoyt-Q0vq-kkgZ-P298-EvNC-RnDs3q
  LV Write Access        read/write
  LV Creation host, time CollinServer, 2013-03-31 16:00:24 -0400
  LV Status              available
  # open                 0
  LV Size                600.00 GiB
  Current LE             153600
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3


```

---

### Post by dcstar on 2013-03-31
Why are user mounts in the /dev tree? that is a System folder.

What is the real mount point for the array?

---

### Post by molnar20 on 2013-03-31
I was following this tutorial as this is my first server set up [http://linuxhomeserverguide.com/server-config/LVM.php](http://linuxhomeserverguide.com/server-config/LVM.php)

---

