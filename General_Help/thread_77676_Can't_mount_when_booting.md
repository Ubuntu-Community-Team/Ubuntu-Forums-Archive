---
title: "Can't mount when booting"
date: 2005-10-17
forum: General Help
---

### Post by mata_svada on 2005-10-17
After removing a Partition I can't boot anymore, eventhough I changed the fstab.
the Message:
```
Loading, please wait... 
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory 
mount: Mounting /dev on /root/dev failed: No such file or directory 
Target filesystem doesn't have /sbin/init
```
my fstab:
```
# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>     <options>          <dump>  <pass> 
proc            /proc           proc       defaults           0       0 
/dev/hda6       /               reiserfs    notail             0       1 
/dev/hda5       none            swap       sw                 0       0 
/dev/hdc        /media/cdrom0   udf,iso9660    ro,user,noauto     0       0 
/dev/fd0        /media/floppy0  auto       rw,user,noauto     0       0
```

and my harddisk
```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/hda 

Disk /dev/hda: 81.9 GB, 81964302336 bytes 
255 heads, 63 sectors/track, 9964 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

   Device Boot      Start         End      Blocks   Id  System 
/dev/hda2               1        9964    80035798+   f  W95 Ext'd (LBA) 
/dev/hda5               1         131     1052194+  82  Linux swap / Solaris 
/dev/hda6            4648        9964    42708771   83  Linux 
/dev/hda7             132        4647    36274738+  83  Linux 

Partition table entries are not in disk order 
```

It would be great if someone could help me.

---

### Post by mata_svada on 2005-10-17
OK, just solved the Problem. I forgot to change the root device in the /boot/grub/menu.lst file.

---

### Post by www.rzr.online.fr on 2006-07-18
> **mata_svada said:**
> 

```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/hda 

Disk /dev/hda: 81.9 GB, 81964302336 bytes 
255 heads, 63 sectors/track, 9964 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

   Device Boot      Start         End      Blocks   Id  System 
/dev/hda2               1        9964    80035798+   f  W95 Ext'd (LBA) 

Partition table entries are not in disk order 
```


I see that you 1st partition starts on hda2 and there is no freespace before ...

How to "rename" it to hda1 because this is driving my grub crazy

---

