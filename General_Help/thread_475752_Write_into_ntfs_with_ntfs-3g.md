---
title: "Write into ntfs with ntfs-3g?"
date: 2007-06-16
forum: General Help
---

### Post by forevereating on 2007-06-16
I can't write into my ntfs partition, I tried running as root and changing permissions but it said it was mounted as a read only drive, how do i mount it as read/write?

---

### Post by merlinus on 2007-06-16
Post results of:

```

cat /etc/fstab

```

And you did install and configure ntfs-3g???

-merlin

---

### Post by forevereating on 2007-06-17
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=891fe065-910a-4f4a-8ba1-2a85262d6f40 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f4848b19-4148-499c-ac44-563876bb6354 /exchange       ext3    defaults        0       2
# /dev/sda4
UUID=67907109-a2d8-458e-bbcd-a25e82dbc98d /home           ext3    defaults        0       2
# /dev/sda1
UUID=3258A18458A14805 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=b1385fda-de05-4b8c-a886-afc2d869061d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom2   udf,iso9660 user,noauto     0       0

```

Just need help with sda1. And lol, I didn't know you could configure ntfs-3g but I did install it, how do I config it?

---

### Post by emid on 2007-06-17
Install ntfs-config with Synaptic.  It provides a gui to configure write access for your NTFS partition.
It should be in Applications-->System Tools, after you install it.

---

### Post by merlinus on 2007-06-17
Applications/System Tools/NTFS Configuration Tool has a few options.  Make sure Enable Write Support is checked.

-merlin

---

### Post by forevereating on 2007-06-17
Can't find it in synaptic. I have multiverse, universe, and restricted enabled.

---

### Post by merlinus on 2007-06-17
Applications/Add Remove.  Select All Open Source Applications from the dropdown menu on the top right, and search for

ntfs-3g

-merlin

---

### Post by Kodfish on 2007-06-18
```
# /dev/sda1
UUID=3258A18458A14805 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```

if the gui fails, make it look like:

```
# /dev/sda1
UUID=3258A18458A14805 /media/sda1     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
```

that should do it, IIRC. if it doesn't, try:

```
umount /media/sda1
mkdir /mnt/sda1
mount -t ntfs-3g /dev/sda1 /mnt/sda1
sudo nautilus /mnt/sda1
```

that should allow you to write files as a temporary fix while you look for the gui configuration. if "mount -t ntfs-3g" doesn't work, try "mount -t ntfs3g"

---

### Post by forevereating on 2007-06-19
Thanks a whole bunch to Kodfish and everyone else for helping me out on this one. You indirectly helped me fix another problem :)

---

