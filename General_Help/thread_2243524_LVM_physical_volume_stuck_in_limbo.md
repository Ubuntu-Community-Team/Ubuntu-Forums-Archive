---
title: "LVM physical volume stuck in limbo"
date: 2014-09-09
forum: General Help
---

### Post by JR_UB on 2014-09-09
I am having trouble with LVM and one of my  physical volumes.

I was trying to set up LVM across two disks (not containing the OS or Home).

First I created the initial Physical Volume, the Volume Group, and the Logical volume, and everything seemed fine.  The problem occurred after trying to add the second disk.  During the course of this, I managed to screw up the entire thing.  Now I have a physical volume that is in a sort of limbo.

If I check the Volume Group, it says /dev/sda is in the volume group. See the end of the following:

```
me@mypc:~$ sudo vgdisplay -v
    Finding all volume groups
  Incorrect metadata area header checksum on /dev/sda at offset 4096
    Finding volume group "lvmglr"
  Incorrect metadata area header checksum on /dev/sda at offset 4096
  --- Volume group ---
  VG Name               lvmglr
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  6
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               6.37 TiB
  PE Size               4.00 MiB
  Total PE              1669257
  Alloc PE / Size       1669257 / 6.37 TiB
  Free  PE / Size       0 / 0
  VG UUID               fo3J0d-4Fx2-aGxs-4LA7-Dd1F-T7EM-4WNcyN

  --- Logical volume ---
  LV Path                /dev/lvmglr/Storage
  LV Name                Storage
  VG Name                lvmglr
  LV UUID                jvRh2S-yfgm-AYQr-z13N-MEHB-lxih-eFx07H
  LV Write Access        read/write
  LV Creation host, time jaypc, 2014-09-07 11:17:18 -0400
  LV Status              available
  # open                 0
  LV Size                6.37 TiB
  Current LE             1669257
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0

  --- Physical volumes ---
  PV Name               /dev/sdg
  PV UUID               JZHnOJ-BXd1-TPHF-udMI-c7lM-4kYz-4yeeB3
  PV Status             allocatable
  Total PE / Free PE    953861 / 0

  PV Name               /dev/sda
  PV UUID               5oMQWz-WreT-OyWd-Oy5b-OrvQ-1YOh-QsnW30
  PV Status             allocatable
  Total PE / Free PE    715396 / 0

```

However, if I check out the physical volume itself, it says it is not in any volume group. So right there it is not consistent, because the Volume Group reports it already contains /dev/sda,  but /dev/sda reports that it is not in any Volume Group:

```
me@mypc:~$ sudo pvdisplay -v /dev/sda
    Using physical volume(s) on command line
  Incorrect metadata area header checksum on /dev/sda at offset 4096
    Wiping cache of LVM-capable devices
  "/dev/sda" is a new physical volume of "2.73 TiB"
  --- NEW Physical volume ---
  PV Name               /dev/sda
  VG Name
  PV Size               2.73 TiB
  Allocatable           NO
  PE Size               0
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               5oMQWz-WreT-OyWd-Oy5b-OrvQ-1YOh-QsnW30
```

It now is impossible to reduce:

```

sudo vgreduce -v lvmglr /dev/sda
    Finding volume group "lvmglr"
  Incorrect metadata area header checksum on /dev/sda at offset 4096
  Incorrect metadata area header checksum on /dev/sda at offset 4096
    Using physical volume(s) on command line
  Physical volume "/dev/sda" still in use

```

Still in use, so I tried the following to move the extants on the drive elsewhere:

```

 sudo pvmove -v -n lvmglr /dev/sda
  Incorrect metadata area header checksum on /dev/sda at offset 4096
    Wiping cache of LVM-capable devices
  Physical volume /dev/sda not in a volume group
  Run `pvmove --help' for more information.

```

This shows /dev/sda not in group.  I can't even force removal:

```

sudo pvremove -v -ff /dev/sda
  Incorrect metadata area header checksum on /dev/sda at offset 4096
    Wiping cache of LVM-capable devices
  Can't open /dev/sda exclusively - not removing. Mounted filesystem?

```

and the file system is definitely not mounted.  

There is also the matter of the metadata header checksum error which I constantly get.

At this point, I am trying to remove /dev/sda from the volume group lvmglr, so I can retry adding it again.

I am looking for any help I can get on this, because now I am stuck and can progress no further.

---

