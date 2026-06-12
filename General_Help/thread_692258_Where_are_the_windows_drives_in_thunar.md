---
title: "Where are the windows drives in thunar"
date: 2008-02-09
forum: General Help
---

### Post by steve196 on 2008-02-09
In nautilus i have the windows drives listed as seperate links next to the file system. Now in Thunar, i don't have that and i also don't find them under /mnt or /media. Where are they?

---

### Post by pointone on 2008-02-09
Post the output of the following command, please:

```
cat /etc/fstab
```

---

### Post by steve196 on 2008-02-10
Obviously i should have posted that. 
But these drives are not in there. Apparently they are mounted by a different mechanism.
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/usr.disk /usr            ext3    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


---

### Post by ingvildr on 2008-02-10
Whats the output of

```
cat /etc/mtab
```

---

### Post by steve196 on 2008-02-10
Thank you!
/etc/mtab says, they are in /media, and that is where they actually are, when gnome is running. Seems, they are just not up when xfce is running instead of gnome.

---

