---
title: "Can't get my External USB drive to Mount!!"
date: 2007-03-18
forum: General Help
---

### Post by bootbat on 2007-03-18
Hi,

I have a triple boot machine with Windows XP, FC6, and Ubuntu Dapper Drake. I have not been able to mount my external USB hard drive to mount in Dapper. It mounts without issues in FC6. Here's what my /etc/fstab looks like:

> proc /proc proc defaults 0 0
/dev/sdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdc1     /media/usbdisk     ntfs-3g     defaults,locale=en_US.UTF-8 0 0
/dev/sdc2    /media/usbdisk-1     ntfs-3g     defaults,locale=en_US.UTF-8 0 0

sdc1 and sdc2 are the USB drives. I followed everything in the following link but cannot get it to work.

[PHP]http://www.ubuntuforums.org/showthread.php?t=217009[/PHP]

My Windows drive mounts fine and appears on the desktop.

When I manually mount as: 

[PHP]mount /dev/sdc1 /media/usbdisk
mount /dev/sdc2 /media/usbdisk-1[/PHP], it appears that it mounts though it does not appear in the desktop. When I  try to open usbdisk and usbdisk-1 under /media, it gives the following error:

> You do not have the permissions necessary to view the contents of "usbdisk-1". for both the drives.

This shouldn't be the case as I use [PHP]su -[/PHP] to get root priviledges. 

Any help is much appreciated!!

---

### Post by bootbat on 2007-03-19
All,

Got this resolved by changing the mount points to /mnt/usbdrive1 and /mnt/usbdrive2. Changed it in /etc/fstab. Mounts well now and appears in the desktop.

Thanks everyone!!

---

