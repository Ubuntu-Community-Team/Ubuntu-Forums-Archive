---
title: "I need some help with fstab..."
date: 2007-10-04
forum: General Help
---

### Post by Hagar55 on 2007-10-04
I am tryint to get an NTFS partition to mount at boot.

This is my current fstab file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=88045bb0-815b-434f-b53e-86153c4cdb20 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=df707aa2-2b63-443d-a09f-26c1ae025782 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda4 /home ext3 nodev,nosuid 0 2

I tried adding this line:
/dev/hda6  media/DSK1_data   auto   ro,user,exec  0   0

I rebooted and the drive diden't mount, neither could I acces it.
Do I have to make the dir DSK1_data first in the /media folder ?
Or am I making some error in the fstab line ?

---

### Post by Jussi Kukkonen on 2007-10-04
> 
Do I have to make the dir DSK1_data first in the /media folder ?
Yes.

---

### Post by McNils on 2007-10-04
> **Hagar55 said:**
> 

I tried adding this line:
/dev/hda6  media/DSK1_data   auto   ro,user,exec  0   0

I rebooted and the drive diden't mount, neither could I acces it.
Do I have to make the dir DSK1_data first in the /media folder ?
Or am I making some error in the fstab line ?


/dev/hda6 /media/DSK1_data ntfs ro,user,exec,auto 0 0

---

### Post by Hagar55 on 2007-10-04
Thanks
Just curious, why do you need to put auto first ?
 
I'll give it a try.

---

### Post by shad0w_walker on 2007-10-04
Just a suggestion, instead of manually editing fstab, install ntfs-3g from the repos. You will want the following packages:

```
ntfs-3g
ntfs-config
```

Install these from the repos and then run

```
gksu ntfs-config
```

This will popup a nice easy dialog to setup your ntfs drives with out the hassle of manually tinkering with fstab. Also gives you full read/write access.

---

### Post by Hagar55 on 2007-10-04
I edited the fstab file.
When I try to acces the partition I get a message saying I don't have the permission/rights to do so.

---

### Post by bodhi.zazen on 2007-10-04
> **Hagar55 said:**
> I edited the fstab file.
When I try to acces the partition I get a message saying I don't have the permission/rights to do so.

See shad0w_walker 's advice re ntfs-config.

You need to set ownership and permissions at the time of mount.

the ntfs driver will give ro access. for rw you need to install ntfs-3g. ntfs-config will install ntfs-3g and a gui config tool

> /dev/hda6 media/DSK1_data ntfs-3g auto,user,exec,uid=1000,gid=100,umask=007 0 2

Will give you rw access.

---

