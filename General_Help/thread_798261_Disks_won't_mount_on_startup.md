---
title: "Disks won't mount on startup"
date: 2008-05-18
forum: General Help
---

### Post by hoozey on 2008-05-18
So now that I've installed Hardy, I can't seem to get other partitions/drives to mount automatically on boot.

When I try this:


```
mount -t vfat -o uid=hoozey,gid=users /dev/sda4 /media/disk
```


It works fine. But when I add it to sessions, it doesn't seem to work. I have to manually mount the disk each time ubuntu starts.

How can I get all of my other partitions and drives to mount automatically whenever I reboot?

---

### Post by cdtech on 2008-05-18
Did you add it to your /etc/fstab file?

---

### Post by JLucien on 2008-05-18
I am experiencing this issue.  I know I need to put an entry in my /etc/fstab file but I do not know the correct syntax.

```
me@mymachine:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc2
UUID=53b781ab-13cb-4dc1-807e-fec2faad9006 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc3
UUID=edf71eb6-5ace-4d27-add7-a5d3fec523dc /boot           ext3    defaults        0       2
# /dev/sdc4
UUID=8c062fbf-2a7d-4bbe-b7ce-a48955b83afa /home           ext3    defaults        0       2
# /dev/sdc1
UUID=6da5d145-b135-4bb1-ae55-5c3b5ccad1bf none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

I need the UUID of my disk.  I have checked dmesg and the GNOME gui, but I cannot find it.  

Any help appreciated.

---

### Post by cdtech on 2008-05-18
Using the command blkid will give you the block id of your device.

What are you trying to mount? ext or ntfs?

---

### Post by JLucien on 2008-05-18
Figured it out. The UUID can be found under System>Preferences>Hardware Information.  Used that and copied my other disk entries, worked a treat!

---

