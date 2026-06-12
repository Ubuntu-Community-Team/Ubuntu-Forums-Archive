---
title: "Safe to resize used partitions?"
date: 2006-12-20
forum: General Help
---

### Post by pickarooney on 2006-12-20
I have a secondary data disk divided into a 140GB partition and a 60GB partition. The 60GB is currently empty and useless while the 140GB is almost full. Is it safe for me to unmount the disk and combine the partition with qtparted? Assuming I delete the smaller one, can I just make the larger one unactive and extend the size of it, or will I risk losing everything that's on it? If there's a risk, I can simply copy data from one partition to the other.

---

### Post by ajgreeny on 2006-12-20
Download a copy of *Gparted liveCD* and burn the iso as a CD image, not just the iso file, but an image.  Start your computer with the CD in the drive and the computer set to boot from CD and you will quickly be into gparted where you can delete the empty partition and then increase the size of the used partition.  If the full partiton is not the forst on the disk you will probably need to move it back to the beginning of the disk first using gparted again, but then you will be able to extend the size by using the slider showing on screen.

Make sure you back up first, just in case, but you should be OK.  Good luck.

---

### Post by pickarooney on 2006-12-20
So in theory it's safe, but... Can't really back up 140GB of the eventuality that it does go wrong, but I might give it a go anyway. So I would definitely need to use a partitioning program from a CD, not from within the OS?

---

### Post by meng on 2006-12-20
I also recommend repartitioning from a live CD, not an installed OS. If you can't backup 140 GB, maybe you can back up the most important items. This is not to disparage the reliability of the GParted LiveCD, it's just that you must be safe, e.g. in case of unfortunately timed power outage.

---

### Post by hal10000 on 2006-12-20
If th disk where you want to rezize the partition is **not** the one whrer your ubuntu system lives in, then you don't need a lifeCD, you can do it with gparted (oe qtparted) in your current system. Just be sure that these partitions are not mounted during operation with gparted: [COLOR="Red"]sudo umount /your/partition1[/COLOR] and [COLOR="Red"]sudo umount /your/partition2[/COLOR]

---

### Post by az on 2006-12-20
Parted is very safe (parted is the backend to all linux partitioning tools, be it qtparted, the gparted live cd or the ubuntu intaller.)

Parted will typically refuse to do something when there is risk of data loss.  Be sure to resize the filesystem as well as the filesystem on it.

Since this is a secondary drive, you don't need to run off a live cd.  You can completely unmount the second hard drive and work on it.

---

### Post by pickarooney on 2006-12-21
I've managed to wipe the small partition, but can't find any option in qtpqrted to expqnd/resize the remaining, larger partition.

---

### Post by meng on 2006-12-21
GParted LiveCD latest version has a wide range of move/resize options for the various filesystems. I'm not sure about QTParted, I've never used it. For the range of options, see here:
[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

---

### Post by pickarooney on 2006-12-21
I installed gparted, and while it has a resize option, it won't let me expand the bigger partition into the free space.

---

### Post by meng on 2006-12-21
Can't you remove /dev/hdb2 altogether?

---

### Post by hikaricore on 2006-12-21
Not to sound silly but you do realize you need to unmount the partition if you're still running your os before it will be possible to resize right?

---

### Post by pickarooney on 2006-12-22
Both partitions of the disk (it's my second HD) are unmounted.
Ehm, feeling stupid now, I just needed to click on the line underneath marked hdb2 and not on the rectangle in the top part of the screen.
Thanks :)

---

### Post by pickarooney on 2006-12-24
OK, finally got the partition extended, after the system crashed twice while trying. Luckily nothing seems to be lost. However, although gparted tells me that /dev/hdb1, mounted at /media/supersize is 189.92GB, bash, krusader etc. tell me that it's still 145GB. I tried umount and mount to see would it change the recognized size, but I think some info in fstab might be telling the OS how many blocks to mount at /dev/hdb1
I haven't rebooted yet, that said.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=23cd75dd-8522-4cc8-8026-43d34facd54f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=38771644-df5d-4863-95ef-4abcf0a9c696 /boot           ext3    defaults        0       2
# /dev/sda4
UUID=6aca9cac-5354-4183-bf88-68e9e62bed9a /home           ext3    defaults        0       2
# /dev/hda6
UUID=f3466d96-c519-11d7-9a37-a027fa319c88 /media/oldhome  ext3    defaults        0       2
# /dev/hda7
UUID=bb8c5418-a024-4cc0-a287-4b1b083042af /media/oldsystem ext3    defaults        0       2
# /dev/hdb1
UUID=f084d777-e5ba-49df-b71b-729b2c0d2475 /media/supersize ext3    defaults        0       2
# /dev/sda5
UUID=7db0edf9-d00d-4b15-a5c3-c738a9091488 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

---

