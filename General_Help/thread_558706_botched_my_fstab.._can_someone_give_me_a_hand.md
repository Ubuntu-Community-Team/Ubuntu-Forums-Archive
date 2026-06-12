---
title: "botched my fstab.. can someone give me a hand"
date: 2007-09-24
forum: General Help
---

### Post by honeydew on 2007-09-24
A day ago.. I was editing my fstab for a virtual machine.. only to find out that I was actually editing my fstab on my actual box.. this means I got rid of all thoose big fancy UIDs.. does anyone know how I would go about repairing that..?  I am not to familiar with uid system yet..  I am kinda hoping to figure them out before I turn my machine off ;).

---

### Post by raul_ on 2007-09-24
Instead of UID  you can use the old /dev/sd<whatever> tags.

Here's mine

```
[raul@icarus ~]$ cat /etc/fstab 
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0


/dev/cdrom /mnt/cdrom   iso9660   ro,user,noauto,unhide   0      0
/dev/cdrom1 /mnt/cdrom1   iso9660   ro,user,noauto,unhide   0      0
/dev/dvd /mnt/dvd   udf   ro,user,noauto,unhide   0      0
/dev/fd0 /mnt/fd0   vfat   user,noauto   0      0
/dev/sda3 swap swap defaults 0 0
/dev/sda5 / ext3 defaults 0 1
/dev/sda6 /home ext3 defaults 0 1

```

---

### Post by Old *ix Geek on 2007-09-24
I'd never looked for it before, but after reading the OP I looked around to see if I could find where the UUID strings are stored.  They're in *device manager* (on KDE); their strings begin with **/org/freedesktop/Hal/devices** and are on the *advanced* tab.  Just look for your hard drive(s) in the left column, then select the one(s) you need UUIDs for, and then look in the right column for its matching entry.

In the future, you'll save yourself a lot of heartache if you simply backup any system (or other important) files before changing them.  It's been my habit for many years to copy **filename** to **filename.orig** (or similar) before editing.  The two seconds it takes to type **cp filename filename.orig** sure beats having to piece things back together when something gets hosed!

---

### Post by honeydew on 2007-09-24
aye.. this is true.. I take such percautions when working on my stable machines.. but I have just been hacking at this guy..  would be nice if there was someway to automaticly make a backup file.. like some type of special flag with vi..  or maybe could write a little script todo this.. that timestamps each old copy with the time it was replaced..   thanks btw.. I think I have my fstab setup for the next boot..

---

