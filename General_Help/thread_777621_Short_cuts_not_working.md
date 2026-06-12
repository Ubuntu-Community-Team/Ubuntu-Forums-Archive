---
title: "Short cuts not working"
date: 2008-05-01
forum: General Help
---

### Post by rules on 2008-05-01
Hi all

I have a couple of short cuts on my desktop which I use to access certain folders on my FAT 32 partition. After a reboot they don't work and I have to got to "Places" on top and select the drive there, after which it will mount it (presumably) and add a short cut on the desktop with the drives name.

Is there no way I can get it to mount this drive at start up and doing so with out creating the short cut?

Thanks.

---

### Post by danwood76 on 2008-05-01
Yes there is.
Add the drive to your fstab.

First we need some info, in terminal post the output of:
```

cat /etc/fstab

```
and:
```

sudo fdisk -l

```
from this we will be able to add the drive to the fstab and get it to automount.

---

### Post by rules on 2008-05-01
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=62a48157-77fd-44fa-b63a-9b3b5053436a /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda8
UUID=aaccc852-110b-41e5-88b6-1a1f67320539 /home           ext3    relatime        0       2
# /dev/hda6
UUID=fca1fb3a-a63f-4734-922e-202d3df30a87 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


 ... and ...


Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5aed5ae

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3824    30716248+   c  W95 FAT32 (LBA)
/dev/hda2            3825        9727    47415847+   f  W95 Ext'd (LBA)
/dev/hda5            3825        7648    30716248+   b  W95 FAT32
/dev/hda6            7649        7777     1036161   82  Linux swap / Solaris
/dev/hda7            7778        8558     6273351   83  Linux
/dev/hda8            8559        9727     9389961   83  Linux

---

### Post by danwood76 on 2008-05-01
Well you have 2 fat partitions, we will add them both.

So the lines we want to add to the fstab will look like this,

First you put the partitions block device, which is /dev/hda1 and /dev/hda5
Then the mount points so /media/HD1 /media/HD2 (you can put what folders you like, just remember to correct the fstab line below)
Then the filesystem, both are fat32 so this is vfat
Then set the default options, followed by two additional options 0 and 0 (dont dump and dont fsck)

So we end up with:
```

/dev/hda1    /media/HD1    vfat    defaults    0    0
/dev/hda5    /media/HD2    vfat    defaults    0    0

```
add these two lines to your fstab by first opening the fstab in gedit with root privileges:
```

sudo gedit /etc/fstab

```

Then just add them as seperate lines to the bottom and save.
We also need to create the mountpoints for the drives to mount to:
```

sudo mkdir /media/HD1
sudo mkdir /media/HD2

```
Ok now you can reboot.
Once it has rebooted you will see the two drives on your desktop,l and probably will need to re create the shortcuts to your folders in your drive, but once they are done they will automount and stay good.

Btw your final fstab should look like this (if you used the mountpoints I suggested):
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda7
UUID=62a48157-77fd-44fa-b63a-9b3b5053436a / ext3 relatime,errors=remount-ro 0 1
# /dev/hda8
UUID=aaccc852-110b-41e5-88b6-1a1f67320539 /home ext3 relatime 0 2
# /dev/hda6
UUID=fca1fb3a-a63f-4734-922e-202d3df30a87 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

/dev/hda1    /media/HD1    vfat    defaults    0    0
/dev/hda5    /media/HD2    vfat    defaults    0    0

```

---

### Post by rules on 2008-05-02
Thanks, works great. Is there a way to not let the mounted drive show up on the desktop though?

---

### Post by jocko on 2008-05-02
> **rules said:**
> Thanks, works great. Is there a way to not let the mounted drive show up on the desktop though?

Make the mount points somewhere else than in /media (e.g. under /mnt)

---

### Post by danwood76 on 2008-05-02
Yep.
So do this:

```

sudo mkdir /mnt/HD1
sudo mkdir /mnt/HD2

```

and change the two fstab lines to be:
```

/dev/hda1    /mnt/HD1    vfat    defaults    0    0
/dev/hda5    /mnt/HD2    vfat    defaults    0    0

```
You will have to recreate the shortcuts.

---

### Post by rules on 2008-05-02
Tried the /mnt route but then the drives disappear completely. Think I'll live with the short cuts on the Desktop.

Thanks again.

---

### Post by danwood76 on 2008-05-02
They dont dissapear completely, you can browse to them through the filesystem.
If you navigate to the /mnt folder you will see them.

You can make gnome not display drives on the desktop also.

---

### Post by rules on 2008-05-02
Where do you "tune" Gnome?

---

### Post by danwood76 on 2008-05-04
in the gconf editor.

press alt + F2 and enter this to launch it:
```

gconf-editor

```

To hide volumes from the desktop you navigate to the nautilus desktop settings.
apps -> nautilus -> desktop
and set volumes_visible to be off, there are quite a few settings you can tweak so it might be worth you looking around the gconf-editor.

By the way this setting will also make CD-Roms invisible from the desktop, they will still be available in places though.

---

### Post by rules on 2008-07-24
Been scratching again the last couple of days and although I can get it to automatically mount the drives (in either /mnt or /media), Thunderbird refuses to "connect" to the local folders directory which is on one of the mounted drives (I have Thunderbird running on XP and Hardy, but I set TB in Hardy to use the same local folders as XP so it's the same mail no matter whic OS you are in). I can see and select the necessary folder, but TB refuses to accept the settings. If I set everything back to normal (have to open needed drive in Nautilus to get it to mount) then TB works perfectly.

Any ideas?

---

### Post by rules on 2008-08-01
What is the difference between forcing it to auto mount (mount when booting) as apposed to going to "Places" and clicking on the drive there so it gets mounted? any difference in permissions on mounted drive?

---

