---
title: "LVM disk missing after power outage - how to check and fix?"
date: 2016-11-03
forum: General Help
---

### Post by lindsayward on 2016-11-03
Thanks in advance for any replies. I really appreciate any help.

Last night some kind of short in my coffee machine caused a power outage. When I turned the power back on, my Ubuntu 14.04 PC greeted me with ```
The disk drive for /movies is not ready or not present.
```

I can skip mounting and it will boot into Ubuntu, but obviously the disk and its contents are not there.
When I use the "Disks" utility I can see that my 2TB Seagate drive (ST2000DM001) reports as a 4GB disk, contents unknown. BIOS also shows the drive at this size.

This disk is part of an LVM logical volume mounted at /movies that also contains 1.8TB of another (WD) disk. I can't access it either due to this problem. I've tried switching cables - same thing. 
Before I get to the boot message and option to skip, I get loads of messages like:
```
status: { DRDY ERR }
error: { ABRT }
failed command: READ DMA

```

Before I list more details, here are my questions:

1. Is there a way to confirm if this disk is dead?

2. If it is dead, how can I get back the part of my LVM logical volume that's on the good disk?

The contents, as the name suggest, is movies and TV recordings, so I don't have a backup and it's not mission critical, unless that mission is relaxing on the couch with one of the few hundred shows I had taped, including most of Community :)

When I boot via USB to gparted, it does not show the disk at all. Why is this and is there a way to get it to show up there?

Stuff that might be helpful:

```
&#10140;  ~ sudo fdisk -l

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d1e6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      976895      487424   83  Linux
/dev/sdc2          976896  3907028991  1953026048   8e  Linux LVM

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe7404ada

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048    39129087    19563520   83  Linux
/dev/sdd2        39131134   234440703    97654785    5  Extended
/dev/sdd5        39131136   234440703    97654784   83  Linux

Disk /dev/mapper/vg-lvroot: 20.0 GB, 19998441472 bytes
255 heads, 63 sectors/track, 2431 cylinders, total 39059456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg-lvroot doesn't contain a valid partition table

Disk /dev/mapper/vg-lvhome: 9999 MB, 9999220736 bytes
255 heads, 63 sectors/track, 1215 cylinders, total 19529728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg-lvhome doesn't contain a valid partition table

Disk /dev/mapper/vg-lvswap: 4999 MB, 4999610368 bytes
255 heads, 63 sectors/track, 607 cylinders, total 9764864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg-lvswap doesn't contain a valid partition table
```


LVM stuff
```

&#10140;  ~ sudo pvs -v
    Scanning for physical volume names
  Couldn't find device with uuid AYUyq4-1YYp-kOK2-FYyB-qRjV-nZKx-vie8lT.
    There are 1 physical volumes missing.
    There are 1 physical volumes missing.
  PV             VG   Fmt  Attr PSize PFree DevSize PV UUID                               
  /dev/sdc2      vg   lvm2 a--  1.82t    0    1.82t XHeIXt-d3xr-Wo1f-rZF9-7rCm-nvey-AfJ0QU
  unknown device vg   lvm2 a-m  1.82t    0       0  AYUyq4-1YYp-kOK2-FYyB-qRjV-nZKx-vie8lT

&#10140;  ~ sudo pvscan 
  Couldn't find device with uuid AYUyq4-1YYp-kOK2-FYyB-qRjV-nZKx-vie8lT.
  PV /dev/sdc2        VG vg   lvm2 [1.82 TiB / 0    free]
  PV unknown device   VG vg   lvm2 [1.82 TiB / 0    free]
  Total: 2 [3.64 TiB] / in use: 2 [3.64 TiB] / in no VG: 0 [0   ]

&#10140;  ~ sudo pvdisplay 
  Couldn't find device with uuid AYUyq4-1YYp-kOK2-FYyB-qRjV-nZKx-vie8lT.
  --- Physical volume ---
  PV Name               /dev/sdc2
  VG Name               vg
  PV Size               1.82 TiB / not usable 4.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              476812
  Free PE               0
  Allocated PE          476812
  PV UUID               XHeIXt-d3xr-Wo1f-rZF9-7rCm-nvey-AfJ0QU
   
  --- Physical volume ---
  PV Name               unknown device
  VG Name               vg
  PV Size               1.82 TiB / not usable 4.09 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              476931
  Free PE               0
  Allocated PE          476931
  PV UUID               AYUyq4-1YYp-kOK2-FYyB-qRjV-nZKx-vie8lT

~ sudo lvdisplay 
  Couldn't find device with uuid AYUyq4-1YYp-kOK2-FYyB-qRjV-nZKx-vie8lT.
  --- Logical volume ---
  LV Path                /dev/vg/lvroot
... snip ...
   
  --- Logical volume ---
  LV Path                /dev/vg/lvmovies
  LV Name                lvmovies
  VG Name                vg
  LV UUID                6Xdubx-0I0S-2dWu-cvNz-2jlU-EUWy-dA7qbr
  LV Write Access        read/write
  LV Creation host, time , 
  LV Status              NOT available
  LV Size                3.61 TiB
  Current LE             945399
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto

 ~ sudo vgdisplay 
  Couldn't find device with uuid AYUyq4-1YYp-kOK2-FYyB-qRjV-nZKx-vie8lT.
  --- Volume group ---
  VG Name               vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  26
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                4
  Open LV               1
  Max PV                0
  Cur PV                2
  Act PV                1
  VG Size               3.64 TiB
  PE Size               4.00 MiB
  Total PE              953743
  Alloc PE / Size       953743 / 3.64 TiB
  Free  PE / Size       0 / 0   
  VG UUID               KoLIJC-xIB9-uKKh-Q7Ba-nfQR-Hf8I-OqsXS5


```

Section from dmesg
```
[  518.772184] ata4.00: failed to set xfermode (err_mask=0x1)
[  518.772188] ata4.00: disabled
[  518.772222] ata4: EH complete
[  518.772493] sd 4:0:0:0: [sdb] Read Capacity(16) failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  518.772498] sd 4:0:0:0: [sdb] Sense not available.
[  518.772534] sd 4:0:0:0: [sdb] Read Capacity(10) failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  518.772538] sd 4:0:0:0: [sdb] Sense not available.
[  518.772601] sdb: detected capacity change from 4142054400 to 0

```

and if I try fsck, I get:
```
 ~ sudo fsck.ext4 -v /dev/sdb
e2fsck 1.42.9 (4-Feb-2014)
fsck.ext4: Invalid argument while trying to open /dev/sdb

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

```
I did try those alternates but with no luck.

I'm really keen to sort this out. My wife has resorted to watching catchup TV on her phone... it's that bad!

Again, thank you so much for any input.

---

### Post by lindsayward on 2016-11-04
Additional info: I have put the disk into a Windows 10 computer and it comes up the same - about 3.6GB. I can run testdisk there or on gparted on that computer and can see the drive at that size, but searching for partitions doesn't seem to do anything.

---

### Post by lindsayward on 2016-11-04
I can't update the firmware (booted to firmware installer via CD, couldn't match drive specific model); I've tried testdisk, R-Studio, and some others... no luck.

So I'll call it dead and I'm on to question 2 now. How do I get my /movies volume to work with the one good disk that is still there?

---

### Post by lindsayward on 2016-11-05
I can run vgchange --partial and then mount /movies and I then I have access to the files that are on the good disk. This is only temporary though (doesn't persist after a reboot).
I'm concerned that [COLOR=#242729][FONT=Consolas]vgreduce --removemissing[/FONT][/COLOR] would actually get rid of my /movies logical volume. 
So how can I make it stay like this - with the movies LV just using the one remaining PV? Is it possible, or do I need to temporarily mount the volume and copy everything to a new drive, then run vgreduce to get rid of the LV, or something else?

---

