---
title: "unable to unmount a drive when non-root"
date: 2006-10-11
forum: General Help
---

### Post by rrwo on 2006-10-11
I have an external USB drive thaat I am no longer able to unmount.

When plugged in, in automatically mounts on "/media/My\ Book"

When I try "umount /media/My\ Book", I get the error "/media/My Book is not in the fstab".  When I use command-line completion with umount, I get "/media/My", which is invalid.

Other commands allow me to access the drive with no problem.

However, I can unmount the drive using "sudo umount /media/My\ Book".

It used to be that I could unmount the drive without sudoing.  Is this possibly because of a kernel update? I am using 2.6.15-27-686.

Also, the drive no longer shows up in Thunar file manager, nor does the icon appear on the desktop (Xfce), when when I browse the filesystem I can access it in /media/My Book.  The drive does show up in Nautilus, but I cannot unmount it from within Nautilus.

---

### Post by Kateikyoushi on 2006-10-11
Interesting could you give me the output of this command ?

```
cat /etc/fstab
```

---

### Post by rrwo on 2006-10-24
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by mjziegle on 2006-10-24
The drive itself is owned by root.  Of course you can't unmount it.  

If you want the drive to be yours create a udev rule.

---

### Post by rrwo on 2006-10-25
Um, as I said in my original post: it used to work as non-root before the upgrade.  My fstab file has not been modified since I installed Ubuntu.  So why does auto-mounting/unmounting no longer work?

---

### Post by rrwo on 2006-10-31
Better yet, I've specified the drives in /etc/pmount.allow. This seems to have fixed the problem.

See [http://ubuntuforums.org/showthread.php?p=1695574#post1695574](http://ubuntuforums.org/showthread.php?p=1695574#post1695574)

---

