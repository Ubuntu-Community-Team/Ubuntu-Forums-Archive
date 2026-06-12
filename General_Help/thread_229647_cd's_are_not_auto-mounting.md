---
title: "cd's are not auto-mounting"
date: 2006-08-04
forum: General Help
---

### Post by Polygon on 2006-08-04
I have found that recently (not caused by any update in particular) that cds do no longer automount. i either have to log off/back in or go to computer and right click the appropirate drive and hit "mount volume"

It seems that this is a problem with only cd's, as my ipod and usb key automount fine.

and yes, i do have "show mounted volumes" selected in the configuration editor

---

### Post by Polygon on 2006-08-05
bump

---

### Post by Polygon on 2006-08-07
bump

---

### Post by orb9220 on 2006-08-07
Post your fstab by opening a term and
gedit /etc/ftab  and copy and pasted here.

Mine says:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
and show up fine when I insert a cd

---

### Post by Polygon on 2006-08-07
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hde1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2 /media/windows/ vfat uid=1000,gid=1000,auto,rw,users 0 0
```

hmm, i see "noauto" next to the two cdrom entries, would changing this to auto fix it?

---

### Post by Sutekh on 2006-08-07
From the [mount man page](http://www.die.net/doc/linux/man/man8/mount.8.html), the **auto** option is used for automatic mounting of filesystems, such as when you use
```
mount -a
```
Which will mount all entries in the /etc/fstab with the **auto** option, those without it are not mounted by the -a command.

I have the same /etc/fstab as both of you guys, and CD's automount.  Sorry I don't think that's the answer you were looking for.

---

### Post by orb9220 on 2006-08-07
If I remember right I had two cdrom drives to and the two lines do not work.

Put a # in front of /dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
and reboot.

That makes the line a comment and dosn't get seen.

Both my drives then worked with the one line,

So
sudo gedit /etc/fstab
put # 
and save.

Hope it works

---

### Post by Polygon on 2006-08-08
that doesnt work, the cd still does not automount and now when i put it in the other cd drive (the one i commented out) it gives me an error when i try to mount it

error: device /dev/hdd is already mounted to /media/cdrecorder

error: could not execute pmount

---

