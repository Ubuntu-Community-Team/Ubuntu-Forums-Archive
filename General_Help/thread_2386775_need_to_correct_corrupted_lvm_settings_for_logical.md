---
title: "need to correct corrupted lvm settings for logical volumes"
date: 2018-03-10
forum: General Help
---

### Post by harterc2 on 2018-03-10
I had 2 luks physical volumes mirrored together.  That created problems during upgrades.
It got so that I could not even mount them.  I have since separated the 2 volumes, and I am able to mount and chroot to one of them.
The other seems to have an unusual size to it.  I want to correct its settings and perhaps resize it to match the one on vg1.  At one time I could not activate one lv even though I had taken off the mirroring.
So I created another vg to salvage my data.
Both pv have data that I don't want destroyed.  So do you see anything unusual in my printouts and how can I fix the config?[CENTER]
[/CENTER]
```
vgdisplay
  WARNING: Device /dev/mapper/crypt-sdb1 has size of 1952318144 sectors which is smaller than corresponding PV size of 3998355945472 sectors. Was device resized?
  One or more devices used as PVs in VG vg0 have changed sizes.
  --- Volume group ---
  VG Name               vg0
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  63
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               1.82 PiB
  PE Size               4.00 MiB
  Total PE              488080559
  Alloc PE / Size       238336 / 931.00 GiB
  Free  PE / Size       487842223 / 1.82 PiB
  VG UUID               YCm8GI-Dard-vLgt-z45d-tOwW-y8jv-rwK3vQ
   
  --- Volume group ---
  VG Name               vg1
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  2
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               930.93 GiB
  PE Size               4.00 MiB
  Total PE              238319
  Alloc PE / Size       238319 / 930.93 GiB
  Free  PE / Size       0 / 0   
  VG UUID               dwtqIg-PDHh-WxYK-GqaG-IGAu-IO7x-WyLS80

lvdisplay
  WARNING: Device /dev/mapper/crypt-sdb1 has size of 1952318144 sectors which is smaller than corresponding PV size of 3998355945472 sectors. Was device resized?
  One or more devices used as PVs in VG vg0 have changed sizes.
  --- Logical volume ---
  LV Path                /dev/vg0/root
  LV Name                root
  VG Name                vg0
  LV UUID                vbL1s6-Lek2-3y9M-dJzd-sHqp-EF11-SuY2xQ
  LV Write Access        read/write
  LV Creation host, time sysresccd, 559220-03-02 03:27:19 +0000
  LV Status              NOT available
  LV Size                931.00 GiB
  Current LE             238336
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  --- Logical volume ---
  LV Path                /dev/vg1/root
  LV Name                root
  VG Name                vg1
  LV UUID                RA9l1t-Pqi1-2iuf-0HsS-mVUi-0t0Q-s03yOC
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2018-03-10 11:41:02 +0000
  LV Status              available
  # open                 1
  LV Size                930.93 GiB
  Current LE             238319
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:3
   
root@ubuntu:/# 

pvdisplay
  WARNING: Device /dev/mapper/crypt-sdb1 has size of 1952318144 sectors which is smaller than corresponding PV size of 3998355945472 sectors. Was device resized?
  One or more devices used as PVs in VG vg0 have changed sizes.
  --- Physical volume ---
  PV Name               /dev/mapper/crypt-sdb1
  VG Name               vg0
  PV Size               1.82 PiB / not usable 3.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              488080559
  Free PE               487842223
  Allocated PE          238336
  PV UUID               C0Xirg-iI2Z-koAz-kR4y-beSy-LLz7-yFXo7f
   
  --- Physical volume ---
  PV Name               /dev/mapper/root2
  VG Name               vg1
  PV Size               930.94 GiB / not usable 4.34 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238319
  Free PE               0
  Allocated PE          238319
  PV UUID               bNwyKm-vdcz-eLBs-4fNc-g2uy-qI7P-9pQ73W
```
   
The root2 pv says that it is full but the ext4 file system is not.

---

### Post by TheFu on 2018-03-10
While the old-school commands are good, I find the newer, summary commands much more helpful.  Especially if posted with '_code tags_' so things line up. Adv-Reply (#).

**pvs**, **vgs**, **lvs**, and **lsblk** are the new-school commands. Having all the important data on 1 screen is helpful for me.

When it comes to issues like these, I tend to wipe everything, restart from the beginning and restore data from a backup.  That lets me fix prior mistakes in a non-trivial setup.

A PV can be fully allocated while anything it contains may have different levels of use. Nothing odd with that, IMHO.

---

### Post by harterc2 on 2018-03-11
I used boot-repair to back up the first part of the partitions.  
But I am afraid it might still have a size of   1.82 PiB / not usable 3.00 MiB.
I had some serious file system damage which caused me to upgrade to 17.10.1 (artfull)
The new school has many commands which provide duplicate information.
Now if I had a gui with each parameter listed and I could change it .......

---

