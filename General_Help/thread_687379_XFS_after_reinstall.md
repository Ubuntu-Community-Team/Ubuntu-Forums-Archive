---
title: "XFS after reinstall"
date: 2008-02-04
forum: General Help
---

### Post by bunkee on 2008-02-04
I had my /home directory on a different drive then my system. My drive with /home is formatted in XFS and spans two drives while my system was ext3. The ext3 drive died and i was forced to replace and reinstall Ubuntu. How do I get my /home drive mounted again?

---

### Post by hyperair on 2008-02-04
Sounds to me like you need to configure your /etc/fstab file. First of all why don't you post the outputs to the following commands:
1. sudo fdisk -l
2. cat /etc/fstab

---

### Post by bunkee on 2008-02-04
First off thank you for your quick reply!  I believe but correct me if I'm wrong that I need to recreate the volume group and logical volume?

output for sudo fdisk -l
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004728e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x636a5917

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

```

output for cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0461101b-08d6-4f97-8329-b16a6385d8cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a826d5eb-d014-412a-beda-d9ee26836e0c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by hyperair on 2008-02-04
Huh no don't create a volume group and whatnot. That's only if you're playing around with LVM2. Something definitely not for the beginner.

Anyway.. I'm assuming that /dev/sdb1 is the partition you intend to become your home directory. So what you do is.. add this line to the bottom of /etc/fstab:
```

/dev/sdb1    /home    xfs   defaults 0 2

```

Now, to get it mounted, restart or use this command: "sudo mount -a"

---

### Post by bunkee on 2008-02-04
I'm pretty sure adding /dev/sdb1    /home    xfs   defaults 0 2 to my fstab is not what i want to do.  My /home spans two drive sdb & sdc

i did something like this back in the day to create my xfs partition
```
pvcreate /dev/sdb1
vgcreate homevg /dev/sdb1
lvcreate -L 743.3G -n homelv homevg
mkfs.xfs /dev/homevg/homelv
pvcreate /dev/sdc
vgextend homevg /dev/sdc
lvextend -L+743.3G /dev/homevg/homelv
mount /home
xfs_growfs /home

```

---

### Post by hyperair on 2008-02-04
._. You're using LVM. That's definite. Okay.... in that case.... run this command and post the output: ```
ls -l /dev/mapper
```

---

### Post by bunkee on 2008-02-04
Oppps Sorry I guess I am using LVM... 
ls -l /dev/mapper
```
ls: /dev/mapper: No such file or directory
```


 sudo vgscan
```
Reading all physical volumes.  This may take a while...
  Couldn't find device with uuid 'WhnDp9-3d8F-8X2C-vSSU-on1K-GeKo-bqziic'.
  Couldn't find all physical volumes for volume group homevg.
  Couldn't find device with uuid 'WhnDp9-3d8F-8X2C-vSSU-on1K-GeKo-bqziic'.
  Couldn't find all physical volumes for volume group homevg.
  Volume group "homevg" not found
```

sudo pvscan
```
Couldn't find device with uuid 'WhnDp9-3d8F-8X2C-vSSU-on1K-GeKo-bqziic'.
  Couldn't find device with uuid 'WhnDp9-3d8F-8X2C-vSSU-on1K-GeKo-bqziic'.
  PV unknown device   VG homevg   lvm2 [698.63 GB / 0    free]
  PV /dev/sdc         VG homevg   lvm2 [698.64 GB / 232.00 MB free]
  Total: 2 [1.36 TB] / in use: 2 [1.36 TB] / in no VG: 0 [0   ]
```

Do I create a new physical volume with  an uuid of 'WhnDp9-3d8F-8X2C-vSSU-on1K-GeKo-bqziic'?

---

