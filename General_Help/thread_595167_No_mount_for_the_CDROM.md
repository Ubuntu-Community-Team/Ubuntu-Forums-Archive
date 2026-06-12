---
title: "No mount for the CDROM"
date: 2007-10-28
forum: General Help
---

### Post by MauroKTM on 2007-10-28
Hallo Guys,

I Have the following problem:

I've installed a 6.10 edgy on a Asus Barebone AMD64bit to be used as Multimedia PC (MythTV, Images, ecc).

The problem is that doesn't mount any CD or DVD or USBdisk

When I insert the cd nothing heappen and the directory /media/cdrom0 remain empty.

If i try to force mount (sudo mount /media/cdrom0) it mount it! but say me that there is a write protection and the device is mount in Read Only mode.

The strange thing is that the cd (That is an ATAPI DVD Rw) ins known as /dev/hdb. Should be scd?

Thnx... for the help

M.

---

### Post by p_quarles on 2007-10-29
If the disk is not an empty CD-R or a CD-R/W, it will automatically mount as read only. Are blank disks mounting as read-only? What about the USB drives? 

Anyway, post the output of this command, and I or someone else may be able to help you:
```
cat /etc/fstab
```

---

### Post by MauroKTM on 2007-11-15
sorry for the delay... this is the resuts:

```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8f5aedcd-6742-48f5-9cc4-0c426e3b99bf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=c5d7079b-25d1-4f33-858b-3816bb39d13f /media/sda3     xfs     defaults        0       2
# /dev/sda2
UUID=941bd4b4-b223-496a-8013-0021ecfd3ccc none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660  user     0       0

```

If I start the computer with the CD inside it mount it. But when I eject and reinsert nothing happen and /media/cdrom reamin empty...

Any idea?

thnx

---

### Post by MauroKTM on 2007-11-21
Hey guys... nobody can help me?

thnx...

---

### Post by p_quarles on 2007-11-21
Hey, meant to get back to you and then forgot. 

Next step would be to try mounting a disk from the command line (if you haven't already). With most CDs, you'll be able to do this without root privileges by typing:
```
mount /media/cdrom0
```If that gives an error stating that you don't have permission, do this as root:
```
sudo mount /media/cdrom0
```

Hopefully, this will make the disk show up on your desktop. Let me know what happens.

---

### Post by MauroKTM on 2007-11-24
It said that will be mount in read only mode...

---

### Post by p_quarles on 2007-11-24
> **MauroKTM said:**
> It said that will be mount in read only mode...
Well, again, unless it's a blank CD-R, it *should* be in read in read-only mode. What about the USB stick?

---

### Post by MauroKTM on 2007-12-01
I don't know why.... I've reinstalled the OS and now all the things are right...

:-?

---

