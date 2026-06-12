---
title: "fstab for separate home partition"
date: 2007-09-02
forum: General Help
---

### Post by imbjr on 2007-09-02
I've just nuked XP and the partition is now holding a /home partition.

However, at the moment, I've got part of fstab like so:

```

# /dev/sda2
UUID=5cb615a9-d8d2-410c-ac93-95beb4607e80 /media/sda2               ext3    defaults,errors=remount-ro 0       1
# /home
/dev/sda2	/home	ext3	nodev,nosuid 0 2

```

Do I really need the /media/sda2 mount? I can't think I'll have much use for it - but will the system bork if I don't?

I could just try it, but the problem may only surface when boot-up comes to do its disk check some days hence.

---

### Post by wmatlock on 2007-09-02
imbjr,

You have made your /home a separate partition is why you need that line in fstab. Look at my fstab below.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=b4f8395d-d1af-45cd-b328-4b8c06880199 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=dbee3578-3606-4101-a724-bcb0dc6c4cb8 /boot           ext3    defaults        0       2
# /dev/hdb1
UUID=fa33f205-ea60-4a0b-8ba6-45707da7f7a4 /home           ext3    defaults        0       2
# /dev/hda2
UUID=45cf9288-7f1c-433d-8a38-1297e5dbb709 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

In my case I have installed Ubuntu using 2 separate drives. The first drive hda is where I put the /boot, /, and swap partitions. The second drive hdb is where I put the /home partition. Now when you boot your system all of these things get pulled together as one file tree in memory starting from the root. 

wmatlock

---

### Post by vanadium on 2007-09-02
It seems indeed that the same drive is mentionned two times in fstab, once with the UUID, the second time with the device name. You better edit the first instance, the one with UUID, and change /media/sda2 to /home. Then remove (place # before it) the last line. It is better to refer to the volumes by their UUID.

---

### Post by imbjr on 2007-09-03
Well, I got rid of the none-home partition spec in fstab and no ill-effects. Me and my PC are now 95% XP free[1].

[1] Got to stop relying on VirtualBox for running Photoshop some day I hope.

This is a Dell PC so it has Dell partitions containing Ghost images of the old XP install. One day I might nuke them too.

---

