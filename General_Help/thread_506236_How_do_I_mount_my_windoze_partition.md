---
title: "How do I mount my windoze partition?"
date: 2007-07-21
forum: General Help
---

### Post by SeattleUser on 2007-07-21
I have ubuntu on a 2nd HD, sdb.  How do I access my windoze stuff on sda?  When I used to use Mandrake linux it would be mounted automatically.   I tried "mount /dev/sda" and I also tried "Computer" in the Places menu.  I realize that I can't write to it, but I would like to access some files.

Thanks

---

### Post by tszanon on 2007-07-21
Try **mount /dev/sda1** instead. If it's not informed in /etc/fstab, you must also specify where it should be mounted:
```
mount /dev/sda1 /media/mywindowspartition
```

---

### Post by SeattleUser on 2007-07-21
I tried
sudo mount /dev/sda1 /media/sda1
and got this message:
 mount: mount point /media/sda1 does not exist

I also tried 
sudo mount /dev/sda1
and got this message:
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

---

### Post by meierfra on 2007-07-21
post the output of

cat  /etc/fstab/

---

### Post by tszanon on 2007-07-21
> **SeattleUser said:**
> I tried
sudo mount /dev/sda1 /media/sda1
and got this message:
 mount: mount point /media/sda1 does not exist

I also tried 
sudo mount /dev/sda1
and got this message:
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

First error message is because /media/sda1 does not exist:
```
sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
```

---

### Post by meierfra on 2007-07-21
Follow these instructions to permanently mount your windows partition ( you can even get write access):

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

---

### Post by SeattleUser on 2007-07-21
Thanks for the tip.  Doing the mkdir first worked. 

It mounts it as owned by root and won't let me see it as a user.  I tried sudo chmod 555 /meda/sda1 and the permissions didn't change.  I looked at the man page for mount and don't see an option to set the permissions to allow other users to access the mount.

---

### Post by SeattleUser on 2007-07-21
Here is my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb9
UUID=dd193bb1-5cfa-400d-a9a8-eb3ecac01816 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb10
UUID=ac83e73c-6258-482e-9d30-5330816f9d42 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by meierfra on 2007-07-21
Since your windows partition isn't listed in /etc/fstab/   it is not mounted during boot-up. Following the link I posted earlier should take care of all your problems.

---

### Post by SeattleUser on 2007-07-21
I wanted to be real careful with the windows drive so I looked at the fstab file for my PCLinuxOS installation and copied the line for sda1 to the ubuntu fstab file.  I still had to do a sudo chmod 777 to the /mnt directory to make it work, though.  It's all working OK now.  Here is the sda section from the fstab file.

# /dev/sda1, size=478865520, type=7: NTFS (primary)
/dev/sda1	/mnt/win_c	ntfs	user,exec,ro,noauto,iocharset=iso8859-1,umask=0	0 0

---

