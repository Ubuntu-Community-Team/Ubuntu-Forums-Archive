---
title: "External HD problems"
date: 2006-12-12
forum: General Help
---

### Post by Pitbull11188 on 2006-12-12
I have had an external hard drive hooked up to my computer for at least a year. It has never given me a problem until now. All of the sudden it is read-only and the root owns it. I am the administrator of the computer and I have no idea how this happened as I am the only user. Though it says read only I can't even see my files, it is listed as 755. I have tried chowning and chmoding but I can't get it to work. Any help would be appreciated. I'm using breezy.

---

### Post by Pitbull11188 on 2006-12-12
jeff@ubuntu:/media$ chmod 777 /media/ieee1394disk
chmod: changing permissions of `/media/ieee1394disk': Operation not permitted
jeff@ubuntu:/media$ chown jeff:jeff /media/ieee1394disk
chown: changing ownership of `/media/ieee1394disk': Operation not permitted
jeff@ubuntu:/media$

[B]
That is what I get when I attempt to chown and chmod the device[/B]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[B]
that is my fstab file contents[/B]

---

### Post by taurus on 2006-12-12
Is it a ntfs, fat32/vfat, or ext2/ext3 filesystem?  And I assume you mount it through /etc/fstab so paste your /etc/fstab here then.

```
cat /etc/fstab
```

---

### Post by taurus on 2006-12-12
You need to use the sudo command if you want to chmod or chown outside your $HOME directory...  How do you mount that external harddrive anyway?

---

### Post by Pitbull11188 on 2006-12-12
It has always auto detected the external hd in the past, I just used sudo and I guess I may be slightly retarded for not hinking of that sooner. I'm going to reboot and see if it works right now.

---

