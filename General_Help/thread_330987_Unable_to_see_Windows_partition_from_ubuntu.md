---
title: "Unable to see Windows partition from ubuntu"
date: 2007-01-03
forum: General Help
---

### Post by icubyx on 2007-01-03
Hi,
I installed ubuntu 6.10 a month ago. My other OS is windows xp. To upgrade to Sp2, I had to update my BIOS. However, after installation of SP2, I cannot find my windows partition mounted on the desktop, nor am I able to access it (which I could before re-installation of SP2). I can however still access my NTFS data partition. 
I have installed ntfs-3g. 
Please help!

---

### Post by taurus on 2007-01-03
What's the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by icubyx on 2007-01-04
[B]hi
Here's what I see on sudo fdisk -l:[/B]


Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2435    19559106    7  HPFS/NTFS
/dev/hda2            2436        4869    19551105    f  W95 Ext'd (LBA)
/dev/hda5            2436        3582     9213246   83  Linux
/dev/hda6            3583        4730     9221278+  83  Linux
/dev/hda7            4731        4869     1116486   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4870    39118243+   7  HPFS/NTFS
---------------------

**And on cat /etc/fstab:**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=b1819157-876d-4fea-88bf-8eb2de5f949f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=231d6234-aeb2-45e8-a39f-3b706913452b /home           ext3    defaults        0       2
# /dev/hda1
UUID=1490929390927AC6 /media/hda1     ntfs-3g    defaults,locale=en_US.utf8    0    0
# /dev/hdb1
UUID=B2C84F6BC84F2CC3 /media/hdb1     ntfs-3g    defaults,locale=en_US.utf8    0    0
# /dev/hda7
UUID=32c9aaf1-cf68-447d-9a00-a25d88a20bcf none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
--------------------------

---

### Post by raul_ on 2007-01-04
I'm assuming you want to mount hdb. What happens if you mount it manually?
```

sudo mount /dev/hdb1

```

---

### Post by jaimz on 2007-01-04
you might want to mount it this way
it's how I mounted mine

[PHP]gksudo nautilus[/PHP]


Then go to;
[PHP]
/mnt[/PHP]

Then make a folder called say;

[PHP]windows[/PHP]

Now go to;
[PHP]
/etc[/PHP]

And open the file called;

[PHP]fstab[/PHP]

Now add a line;

[PHP]/dev/hda1       /mnt/windows  ntfs    nls=utf8,umask=0222 0       0[/PHP]

Where hda1 will be whatever Windows is actually on (usually hda1 as it happens).

Now close the Nautilus. Then open a terminal and type;

[PHP]sudo mount -a[/PHP]

This will mount the new fstab file. Navigate your way with normal Nautilus to;

[PHP]/mnt/Windows[/PHP]

And you will see your Windows files

if you're using a sata drive, it'll be sda1

---

### Post by icubyx on 2007-01-05
Its been fixed. The UUID mentioned in fstab didn't match the hda1 UUID. 
Apparently, it changes if I re-install windows after a format...?
So I went to /dev/disk/by-uuid and replaced the hda1 UUID into the fstab hda1 entry.
It works well now. Thanks for your suggestions :)

---

