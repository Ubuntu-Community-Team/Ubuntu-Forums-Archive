---
title: "auto mount iso image with fstab"
date: 2007-01-01
forum: General Help
---

### Post by precinto on 2007-01-01
Hello.

I need some help getting this two cd iso images automounted on startup. I've modified the /etc/fstab like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/home/car/r/I.iso	/home/car/r/I	udf,iso9660 user,noauto,loop	0	0
/home/car/r/II.iso	/home/car/r/II	udf,iso9660 user,noauto,loop	0	0

```

However upon restarting or using 'sudo mount -a' nothing happens. I've noticed though that if I do 'sudo mount /home/car/I' (or II) it gets mounted without problem.

What am I doing wrong? 

Thanks a lot.

---

### Post by pseudonym on 2007-01-01
> **precinto said:**
> 

/home/car/r/I.iso	/home/car/r/I	udf,iso9660 user,noauto,loop	0	0
/home/car/r/II.iso	/home/car/r/II	udf,iso9660 user,noauto,loop	0	0
[/CODE]
What am I doing wrong? 
It's because you've specified 'noauto' as an option. That prevents anything from being mounted non-explicitly ie. at startup, or via 'sudo mount -a'.

---

### Post by meng on 2007-01-01
Exactly. The reason your CD-ROM _drive_ is specified noauto is to avoid wasting time by trying to mount a drive that may be empty!

---

### Post by precinto on 2007-01-01
you guys are really troubleshooting, thanks a lot.

---

