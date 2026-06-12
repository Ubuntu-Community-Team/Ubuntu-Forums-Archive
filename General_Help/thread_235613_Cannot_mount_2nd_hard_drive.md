---
title: "Cannot mount 2nd hard drive"
date: 2006-08-13
forum: General Help
---

### Post by MJSOnline on 2006-08-13
Hi all.  I am having trouble mounting my 2nd hard drive in Dapper.  Below is my fdisk result.


Disk /dev/hda: 10.2 GB, 10204766208 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1185     9518481   83  Linux
/dev/hda2            1186        1240      441787+   5  Extended
/dev/hda5            1186        1240      441756   82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9964    80035798+  83  Linux


Below is a copy of my fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb       /media/SD	ext3		defaults			0	0

The drive does have data on it from before, around 20 gigs' worth.  How do I auto-mount it at bootup? 

Anyone got any ideas? Thanks M

---

### Post by vijirajan on 2006-08-13
You can auto mount it by adding an entry for it in the /etc/fstab. Add the following line at the end of /etc/fstab:

/dev/hdb1 /mount/data ext3 defaults,errors=remount-ro 0 0

NOTE: you can change /mount/data above to any directory you want. This is where the second hard disk is going to be mounter.

Hope this helps!

---

### Post by vijirajan on 2006-08-13
I think this line in your /etc/fstab
```

/dev/hdb /media/SD ext3 defaults 0 0

```

should probably be
```

/dev/[COLOR="Red"]hdb1[/COLOR] /media/SD ext3 defaults 0 0

```

---

### Post by MJSOnline on 2006-08-13
I have the error of "mount: only root can mount /dev/hdb1 on /media/s"  What do I do? M

---

### Post by vijirajan on 2006-08-13
Are you trying to mount it manually. If so run,
```

sudo mount -a

```

The next time you reboot your computer it should automatically mount that hard drive.

---

### Post by MJSOnline on 2006-08-13
Nope that just came back with this error  "sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

Any ideas? IUf you can from the top. Thanks. M

---

### Post by vijirajan on 2006-08-13
It looks like /dev/hdb1 is not a ext3 file system. Are you sure it is ext3? When and how did u create that ext3 partition on your second hard drive?

---

### Post by MJSOnline on 2006-08-13
I created it in the last 6 months under Badger.  How do I check it out then? M

---

### Post by vijirajan on 2006-08-13
Looks like the partition has errors. Execute the following command to fix errors:

```

sudo e2fsck -p /dev/hdb1

```

Look for warnings from the above command, if it says its not safe to execute the command, don't execute it. Let me know what happened.

---

