---
title: "second hard drive - permissions"
date: 2007-07-06
forum: General Help
---

### Post by Kevin the Olden on 2007-07-06
Hello all..

How do I set permissions for a second hard drive? I cannot log in as root (says that's not allowed) and if I do su I can't find the drive anyway, not under /mnt

Any help greatly appreciated...

Kevin (In Australia)

---

### Post by Cresho on 2007-07-06
sudo for root user

create a directory such as "my_disk" and mount it in this form

mount /dev/hda1 /media/my_disk

you will also need to play with the permissions.

---

### Post by NeoLithium on 2007-07-06
Is the hard drive mounted? Can you post the output of ```
cat /etc/fstab
``` and which relevant drive it is on there? If not we can always help mounting it with write pemissions. also include the filesystem that it is, be it Linux or NTFS or FAT, etc.

---

### Post by Kevin the Olden on 2007-07-06
> **Cresho said:**
> sudo for root user

create a directory such as "my_disk" and mount it in this form

mount /dev/hda1 /media/my_disk

you will also need to play with the permissions.
File system is NTFS

fstab....

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1215253d-ba71-416e-a420-48dd1a3eb12a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=43fc9589-7772-4d81-85ff-e1878b90209b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by confused57 on 2007-07-06
Maybe this will help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Cresho on 2007-07-06
There is two programs I use to manually mount the drive after boot up but I chose the using text editor to automount my drives by modifying fstab.


this first part is the easy way.

install from "add and remove" under applications.
1. ntfs configuration tool
2. if you right click on the taskbar, add program called "disk mounter" and it will add a spot to where you can tell it to mount or unmount drives.  It will tell you drives which are not mounted as well.

ohh yeah!  try the tutorial cunfused57 posted.

---

### Post by xc3RnbFO8P on 2007-07-06
Try to Install NTFS in "add and remove" (all available application).

---

### Post by Kevin the Olden on 2007-07-06
Solved. I downloaded the NTFS configuration tool. Now I can move all my Dr Who episodes off my main disk. Thanks one and all.

Kevin the Olden

---

