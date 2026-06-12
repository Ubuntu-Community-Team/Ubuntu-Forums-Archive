---
title: "Lubuntu 12.10 -- LVM LV not mounting rw. Why?"
date: 2013-04-01
forum: General Help
---

### Post by blenderfox on 2013-04-01
Hi all, I'm trying to mount my USB drive (which contains a PV and VG), and it mounts, but I can't seem to write anything into it. Here's the stats from my LVM configuration:

```
lvm> pvdisplay
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               HitachiVG
  PV Size               931.51 GiB / not usable 4.97 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238466
  Free PE               0
  Allocated PE          238466
  PV UUID               3hWNvv-qToJ-3f26-IrTV-P202-QMNI-laGJ33


lvm> lvdisplay
  --- Logical volume ---
  LV Path                /dev/HitachiVG/Hitachi
  LV Name                Hitachi
  VG Name                HitachiVG
  LV UUID                sCBLGe-tPGs-gI5Q-RfTt-WH8X-ZSOh-fY2g6j
  LV Write Access        read/write
  LV Creation host, time Dimension-2400, 2013-04-01 14:42:40 +0100
  LV Status              available
  # open                 0
  LV Size                931.51 GiB
  Current LE             238466
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
```

And here's what happens when I try to mount to a temp folder and create another folder inside it: 
```
$ mkdir temp
$ sudo mount /dev/HitachiVG/Hitachi temp
$ mkdir temp/temp
mkdir: cannot create directory `temp/temp': Permission denied
```

And where's what I happens when I specifically tell mount to mount the LV read-write
```
$ sudo umount temp$ sudo mount -o rw /dev/HitachiVG/Hitachi temp
$ mkdir temp/temp
mkdir: cannot create directory `temp/temp': Permission denied
```

So no matter what I pass in, I can't seem to write to the mount folder. This includes when I put the options into the fstab.

Does anyone know why that even though the LV registers as read/write, and even though I mount as read/write, I can't write to the folder even though it mounted successfully?

---

### Post by blenderfox on 2013-04-01
Never mind, found the solution, I had to

```
sudo chmod 777 temp
```

To enable writing, and this held on the next reboot. It even held when I changed the mount location

---

