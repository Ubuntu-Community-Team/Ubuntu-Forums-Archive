---
title: "cant write to usb harddrive"
date: 2007-01-28
forum: General Help
---

### Post by shickidyshade on 2007-01-28
can't write to my external usb hard drive which has been used as a windows before

here is my fdisk -l but i dont think its going to work 
```
isk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

```

---

### Post by yigal.weinstein on 2007-01-28
What partition(s) are you mounting?  Are you letting Gnome automount or what is in your /media folder?

---

### Post by etank on 2007-01-28
If you don't have it installed then get ntfs-3g. Once that is installed you should be able to write to your NTFS drive once the fstab file is set up to allow for it. Here is how mine looks:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=dfbf608d-cba0-426d-a607-135086d7f6e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc2
UUID=859bda67-3959-4d4e-b07d-f19c442a0266 /home           ext3    defaults        0       2
# /dev/hdc3
UUID=b419155b-94e6-46c1-b56f-36cf4ad0a8b5 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda1     /media/usbdrive     ntfs-3g     users,silent,umask=0002,locale=en_US.utf8,no_def_opts,allow_other    0    0
```
This allows my drive to be auto mounted using ntfs-3g to /media/usbdrive. I think you also have to add your user account to the fuse group and then do:
```
sudo chown root:fuse /media/usbdrive
```
and
```
sudo chmod g+w /media/usbdrive
```

---

### Post by shickidyshade on 2007-01-28
it is being automounted via ubuntu 

this is my fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3dd99d78-8cac-406d-82eb-8097aa809019 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c14b5db5-5957-4724-9cba-7b40c4584e03 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

attached is a screenshot of my media portion of my filesystem

---

### Post by Buck2348 on 2007-01-28
Is it sdb or sdc that you're trying to write to?

---

### Post by shickidyshade on 2007-01-28
> **shickidyshade said:**
> can't write to my external usb hard drive which has been used as a windows before

here is my fdisk -l but i dont think its going to work 
```
isk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

```


Im guessing sdc based on this

---

### Post by Buck2348 on 2007-01-28
If it's sdc, it's normal not to be able to write to it because Ubuntu doesn't support writing to ntfs.  [This thread]("http://www.ubuntuforums.org/showthread.php?t=217009") will show you how to enable writing to it--not very difficult.

I have no idea what might be the trouble with sdb--"no valid partition table."  If there is nothing on the disk that you want to save you can partition it using gparted.  Otherwise, I don't know . . .

Buck

---

### Post by yigal.weinstein on 2007-01-28
FAT32 is another way to go.

I use a 1GB FAT32 usb flash disk and it works perfectly on Windows XP and Ubuntu and I am pretty sure for Vista also although if I can help it I won't be touching Vista, ever.  No additional software is required to read and write to this type of device  (It works on Mac. but who cares).

---

