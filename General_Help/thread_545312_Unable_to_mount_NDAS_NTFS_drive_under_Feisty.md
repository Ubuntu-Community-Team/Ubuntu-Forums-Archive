---
title: "Unable to mount NDAS NTFS drive under Feisty"
date: 2007-09-07
forum: General Help
---

### Post by diskace on 2007-09-07
Hi folks, this is my first post here. I am having a very hard time loading a NDAS drive that is running an NTFS partition under Feisty.

```

root@fixit-laptop:/dev# fdisk -l /dev/ndas-00526367-0

Disk /dev/ndas-00526367-0: 320.0 GB, 320070836224 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                Device Boot      Start         End      Blocks   Id  System
/dev/ndas-00526367-0p1               1       38912   312560608+   7  HPFS/NTFS


```

I am using Ximeta netdisk linux drivers to be able to attach the NDAS drive. I can see the disk so this part is working fine.

```

root@fixit-laptop:/dev# cat /proc/ndas/devs
Name            ID                     Key Serial           Ver Status         Slots
NetDisk1        0T3F66H3Y8RL9DU*****   Yes 00526367         1   Online         1

```

My problems start here:

When i try to mount the new drive under my linux distribution i get an error.

I installed ntfs-3G but it's still not working properly for me.

Here is a copy of my fstab output

```

/dev/ndas-00526367-0 /media/netdisk ntfs-3g defaults,locale=en_US.utf8   0    0

```

The error message when i try manually:

```

root@fixit-laptop:/dev# mount -t ntfs-3g /dev/ndas-00526367-0 /media/netdisk/
NTFS signature is missing.
Failed to startup volume: Argument invalide
Failed to mount '/dev/ndas-00526367-0': Argument invalide
The device '/dev/ndas-00526367-0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

I know that i might be only a few steps away of using my NDAS. Can anyone help me out with this issue ? It would be very appreciated. Thanks.

---

### Post by diskace on 2007-09-07
anyone ? I can't access this drive. Thanks

---

### Post by diskace on 2007-09-08
i really need to get this thing work. Can anyone chime in ?

---

### Post by merlinus on 2007-09-08
From what I see, you are attempting to mount a drive, not a partition, and so it is not working.

You might try running and post results of:

```

sudo fdisk -l

```or reformat the drive and create a partition.

-merlin

---

### Post by diskace on 2007-09-11
Hi merlin, you were right.

Here is what i did to resolv the problem:

```

cfdisk /dev/ndas-00526367-0 

```

I created a table partition of 

1 NTFS of 20G bootable flag
1 EXT3 300 G

Writed partition table to disk

apt-get gparted

launched gparted

Formatted both partitions

mount -t ext3 /dev/ndas-00526367-0p1 /media/netdisk
mount -t ntfs /dev/ndas-00526367-0p2 /media/windows

---

