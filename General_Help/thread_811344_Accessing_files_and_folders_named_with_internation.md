---
title: "Accessing files and folders named with international characters on NTFS mount"
date: 2008-05-29
forum: General Help
---

### Post by Antillean on 2008-05-29
Hey

I'm running a Windows Vista/Ubuntu 8.04 dual boot. Ubuntu was installed with Wubi. 

I can't seem to access files and folders on my Windows NTFS partition whose names contain non-English characters (such as ñ). Nautilus doesn't show them. I also tried creating a folder on my NTFS partition with one of these characters ("Niña") and got the error message:

> The item could not be renamed.
The name "Niña" is already used in this folder. Please use a different name.

There is no other folder in that directory with that name.

How do I fix this?

---

### Post by Antillean on 2008-05-31
Anyone?

---

### Post by quelx on 2008-05-31
[http://ubuntuforums.org/showpost.php?p=41878&postcount=7](http://ubuntuforums.org/showpost.php?p=41878&postcount=7)

---

### Post by Antillean on 2008-06-02
Thanks.

I don't think I see the host NTFS partition here though. Here's my /etc/fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by Antillean on 2008-06-06
Anyone?

---

### Post by gurlinux on 2008-09-03
This might help:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4759465](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4759465)

(in fact, I'm trying it tonight myself)

---

