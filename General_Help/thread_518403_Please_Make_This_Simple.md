---
title: "Please Make This Simple"
date: 2007-08-05
forum: General Help
---

### Post by joeinazyes on 2007-08-05
I have two internal hard disks, hda and hdb.  hdb is FAT32.  I want it to automatically mount on startup with read and write permissions.  PLEASE do not point me to some other forum posting, I think I have been to them all.  PLEASE DO read my fstab file posted below and display the correct entry for boot up that will accomplish what I want.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3c00a505-4c9f-4205-a303-c44314fc8bf0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=00c52fa0-37cc-4083-8bea-6bb3ac348429 none            swap    sw              0       0
/dev/hdb	/media/hdb	auto,users,async,exec,dev,suid,rw,mode=777,umask=000
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Thank you.

---

### Post by meierfra on 2007-08-05
Please post the output of

```
sudo fdisk -l
```

---

### Post by joeinazyes on 2007-08-05
Ahh, this may be the problem...

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9598    77095903+  83  Linux
/dev/hda2            9599       10011     3317422+   5  Extended
/dev/hda5            9599       10011     3317391   82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdb doesn't contain a valid partition table

My hdb drive seems to have a corrupt partition table.  Is there any way to repair the partition table and save the data that is on the disk?

---

### Post by meierfra on 2007-08-06
I don't know enough about hard drives to help you with the partition table problem. But  I can tell you 
the correct way to mount your Fat32 partition ( assuming that your 2nd hard drive only contains one partition:

Replace the line
 /dev/hdb /media/hdb auto,users,async,exec,dev,suid,rw,mode=777,umask=0 00
in your fstab by

>  /dev/hdb1    /media/name_of_your_choice   vfat  iocharset=utf8,umask=000  0    0

Create  the  directory /media/name_of_your_choice  via

```
sudo mkdir /media/name_of_your_choice 
``` 
and reboot.
(I'm not sure how many  mistakes  you had in your  fstab, but  "/dev/hdb"  is definitely wrong and needs to be replaced by  " /dev/hdb1")

It probably won't work, because of your partition table problem.  But I think its worth a try.

---

### Post by joeinazyes on 2007-08-06
Thanks meierfra,

Once I get the Partition Table problem solved OR reformat my drive, your fstab entry is exactly what I was looking for.  Also, the fdisk command helped get at the problem in the first place.

Thanks.

Joe

---

