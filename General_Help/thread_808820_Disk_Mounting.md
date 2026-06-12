---
title: "Disk Mounting"
date: 2008-05-26
forum: General Help
---

### Post by melenor on 2008-05-26
In ubuntu 7.10 when i booted up the disks would automatically mount, and when ever i plug in a thumb drive they too would mount. no nothing mounts until i go to computer and right click mount or double-click, is there any way to make this go the way it used to be.

---

### Post by cdtech on 2008-05-26
Sure, you can add them to the /etc/fstab

I'll be right back....

---

### Post by cdtech on 2008-05-26
What do you get with:
sudo fdisk -l

and:
cat /etc/fstab

---

### Post by melenor on 2008-05-26
> **cdtech said:**
> What do you get with:
sudo fdisk -l

and:
cat /etc/fstab

What exactly does that do and will it automatically mount when i log in, or when i plug it in?

---

### Post by VMC on 2008-05-26
> **melenor said:**
> What exactly does that do and will it automatically mount when i log in, or when i plug it in?

'fdisk -l' will show us your hard drive layout.
'fstab' is how partitions are mounted, among other things.

---

### Post by cdtech on 2008-05-26
That will show us your disk order and what mounts at boot with the fstab

You'll need to know which disk to mount or put into the fstab file, thats why you need to show sudo fdisk -l

---

### Post by melenor on 2008-05-26
*fdisk -l* gave me this

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009fe94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6788    54524578+  83  Linux
/dev/sda2            6789       30401   189671422+   5  Extended
/dev/sda5            6789       30285   188739621    b  W95 FAT32
/dev/sda6           30286       30401      931738+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40d3549b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30515   245111706    b  W95 FAT32

Disk /dev/sdc: 4126 MB, 4126146560 bytes
16 heads, 32 sectors/track, 15740 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x9bea1c7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       15740     4029424    b  W95 FAT32


while *cat /etc/fstab * gave me 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0899106b-1bd9-4da0-8e49-a43ae0a2b4c4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=ffe3dc94-2eed-4eb7-acd4-cfe0bbb8cc7f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by cdtech on 2008-05-26
So your sdb and sdc are your USB device's?

Your sda5 is a partition you can mount with fstab with an entry:
/dev/sda5 /mnt/sda5     vfat    defaults,umask=007,gid=46 0       1

Try to restart hal:
sudo /etc/init.d/hal restart
Restarting Hardware abstraction layer: hald.

I've seen some users have to reinstall hal do to this issue.
sudo apt-get remove hal
sudo apt-get install hal

---

### Post by melenor on 2008-05-26
no my sdb is my second drive, that i also want to mount, the sdc is the USB device.
Does it matter where i add the line, because i added it above the CD Drive, and floppy (which i don't have and never did have).

---

### Post by cdtech on 2008-05-26
> **melenor said:**
> no my sdb is my second drive, that i also want to mount, the sdc is the USB device.
Does it matter where i add the line, because i added it above the CD Drive, and floppy (which i don't have and never did have).

No thats good.

You can do the same with the sdb1 device as well.

---

### Post by melenor on 2008-05-26
so just put in 
/dev/sdb1 /mnt/sda5 vfat defaults,umask=007,gid=46 0 1

---

### Post by melenor on 2008-05-29
it didn't work, the hard drive doesn't mount automatically, when i log in.

---

