---
title: "Need help mounting second disk"
date: 2006-12-28
forum: General Help
---

### Post by lucid on 2006-12-28
I dual boot Edgy on one disc, and Dapper on the second. I've looked around for a way to access the Dapper drive but to no avail so far. Is there a fast and easy way to mount it from Edgy?

This is the output from fdisk -l if it helps:
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 15.3 GB, 15364339200 bytes
255 heads, 63 sectors/track, 1867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1787    14354046   83  Linux
/dev/hdb2            1788        1867      642600    5  Extended
/dev/hdb5            1788        1867      642568+  82  Linux swap / Solaris

---

### Post by kidders on 2006-12-28
Hi there,

The way to access filesystems in Linux is always the same...

Eg: **mount /dev/hdb1 /mnt/somewhere**

If you add a line to your /etc/fstab for a specific filesystem, you can reduce the command to **mount /dev/hdb1** or **mount /mnt/somewhere** ... or have it happen automatically, if you like.

Are you having a specific problem with Dapper's filesystem?

---

### Post by lucid on 2006-12-31
Thanks for the help. :)

No problem with the Dapper file system; it is more that I was having trouble finding out the best way to go about mounting the second drive. For example, the ubuntu wiki steered me to a menu item that doesn't exist, another section had me fiddling with a file which governs access to partitions which didn't work, that kind of thing.

---

### Post by po0f on 2006-12-31
lucid,

An entry along the lines of:
```
[FONT="Courier New"]/dev/hdb1 /media/dapper ext3 defaults,user 0 0[/FONT]
```
should mount it automatically for you under Edgy, provided the partition is formatted as ext3.  To make sure everyone can read it (before you mount it):
```
[FONT="Courier New"]$ sudo mkdir /media/dapper # create directory
$ sudo chmod 666 /media/dapper # global read/write, the directories underneath will have old permissions
$ sudo mount -a # mount all auto filesystems (or just mount /media/dapper[/FONT]
```

Wikis are evil, don't trust them.

---

