---
title: "Second hardrive not found"
date: 2007-02-16
forum: General Help
---

### Post by garfunkle on 2007-02-16
I've just switched from windows to Linux this week and so far its almost perfect, i have everything working apart from this problem.
When i installed linux it all worked fine, but when i went to the computer it could only see one of my two hardrives. I have linux installed on the master drive and the slave drive is the one that cannot be found.

This is a screenshot of "sudo fdisk -l" which shows that it knows the drive is there. Is there a way to get linux to recognise that its there. Again i'm new at linux so thats probably why i don't know what to do. 

Thanks to anyone that can help.

---

### Post by stalker145 on 2007-02-16
> **garfunkle said:**
> Is there a way to get linux to recognise that its there.

Here's a couple of good places to start. aysiu always has good info on his page.

[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

A lot of what you'll put in your fstab file depends on what file system you're using. Check back if this doens't fix things for you. 

Oh, yeah, and welcome to Ubuntu :)

---

### Post by garfunkle on 2007-02-16
Lol, thanks for the welcome

But it didn't seem to work. I'm not sure if its because i'm not doing it right or something else. Is there more information i can give you that will help find the problem?

*edit, linux now recognises it (when typing in "sudo fdisk -l")
But it doesn't show up  in computer.

*edit again*
On that site you linked me to it said to create the directory /windows. Does this mean that that directory is the actual hardrive?

---

### Post by taurus on 2007-02-16
What's the output of that command and the content of your /etc/fstab?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by garfunkle on 2007-02-16
sudo fdisk -l :

```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4997    40138371    7  HPFS/NTFS

```

and cat /etc/fstab :

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=01151aca-17bf-4e73-b494-b0a033d5abc1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=b1fe3de1-b520-4713-a1ff-d9a619f0995a none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by garfunkle on 2007-02-16
This topic fell down a few pages so i thought i'd bump it up. If this isn't allowed just let me know.

---

### Post by taurus on 2007-02-16
Anything for our friend in Scotland.  (Know a mate in Montrose.)


Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

