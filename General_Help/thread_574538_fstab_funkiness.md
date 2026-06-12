---
title: "fstab funkiness"
date: 2007-10-12
forum: General Help
---

### Post by sippyCUP on 2007-10-12
I recently reformatted my external disk from ntfs to ext3 and needed to modify fstab to automount it. My fstab is posted at the end.

 What's weird is that ubuntu is not mounting my partitions where I ask it to. If I change the ntfs partition's mount point to /media/windows, it won't automount at all. And even though the last entry's mount point is clearly specified as /media/300, it's always mounted at /media/disk. What gives?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=137cc1dc-9164-4b97-8c78-94beaefd0be3 /               ext3    defaults,errors=remount-ro 0       1
# windowsxp
UUID=BECC835ECC830FB7 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=6d6d3128-dd3f-42c1-8984-3dc6aa6b49bc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec     0       0
UUID=dc85c059-9011-4704-984f-5239695ae4e5 /media/300 ext3 0 1

---

### Post by kerry_s on 2007-10-12
do you have a "windows folder" in /media.
when you change the mount point you have to have the folder to match.

---

### Post by sippyCUP on 2007-10-13
I thought that might be it but in /media I created a directory called 300 before adding that device I wanted to mount there to fstab. Alas, 300 no longer exists there. Does Ubuntu wipe that directory on shutdown or boot, or otherwise treat its contents as virtual files?

---

### Post by bodhi.zazen on 2007-10-13
removable devices are handled by gnome-volume-manager (GVM)

When you insert a device into a usb slot GVM automagically makes a mount point and mounts the device setting ownership and permissions.

If you add the device to fstab you are circumventing the magic and so must set up the mount point ...

If a device was mounted by GVM the mount point persists until you log off (to the log in screen) or sometimes re-boot.

---

