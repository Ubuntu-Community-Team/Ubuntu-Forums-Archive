---
title: "only root can see windows partition?"
date: 2007-05-13
forum: General Help
---

### Post by m.musashi on 2007-05-13
After installing feisty I've noticed that in order to see the contents of my windows partition (vista) I have to be an administrator. I get a dialog saying it's restricted for security reasons and to enter my password.

I've never seen this before. Is this a new default setting for feisty? Can I change it? I've checked my fstab but I don't see anything obvious. It has the same settings as another ntfs partition.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c57c46cc-e83c-4c52-bb67-1708fe6ee838 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=986b2001-e09c-465d-beb1-aa83fe2fc084 /home           ext3    defaults        0       2
# /dev/sdb1
UUID=2D7322CB03EBAD27 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=92d08074-a22d-4536-912a-d81c2c68bffe /media/sdb5     ext3    defaults        0       2
# /dev/sdb6
UUID=e8ea70a1-8dfc-4267-a177-56901e957475 /media/sdb6     ext3    defaults        0       2
# /dev/sdb8
UUID=3CAC121CAC11D16E /media/sdb8     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=0FA98EF54F964DD7 /media/vista    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=1920b0ea-86cf-47ca-9bdf-435657c1d3a1 none            swap    sw              0       0
# /dev/sdb7
UUID=3f623bd5-c24a-40c3-9fac-9aef3ce1f1a0 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
```

Thanks for any help.

---

### Post by happybrick on 2007-05-19
Have you installed the NTFS Configuration Tool?

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by m.musashi on 2007-05-19
No, I did not install the tool. I have never used it before and never had a problem reading an NTFS partition. My understanding was that reading NTFS required nothing special. In fact, I can read the partition but now I have to give my password where as I never did before. Not that it's a big problem. It's just a change and I'd like to understand why.

Thanks.

---

