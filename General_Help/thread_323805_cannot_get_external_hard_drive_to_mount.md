---
title: "cannot get external hard drive to mount"
date: 2006-12-22
forum: General Help
---

### Post by dasuberdog on 2006-12-22
I finally got my new external hard drive formated in fat32 and now I cannot remount it.....

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1144     9189148+  83  Linux
/dev/hda2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/hda3            1145        1275     1052257+  82  Linux swap / Solaris
/dev/hda5            1276        9728    67898691    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    b  W95 FAT32
scribble@Scribble:~$ sudo mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
scribble@Scribble:~$

---

### Post by bodhi.zazen on 2006-12-22
sudo mkdir /media/usb
sudo mount /dev/sda1 /media/usb -o umask=000

---

### Post by eriefisher on 2006-12-22
first sudo mkdir /yourmountpount(your choice)

then you will have insert a line in the fstab to reflect the drive.

sudo gedit /etc/fstab

/dev/sda1     /mount/point            vfat    iocharset=utf8,umask=000,uid=1000,gid=1000,auto,rw,nouser   0       0

---

### Post by dasuberdog on 2006-12-23
> **bodhi.zazen said:**
> sudo mkdir /media/usb
sudo mount /dev/sda1 /media/usb -o umask=000

I did that

scribble@Scribble:~$ sudo mkdir /media/usb
Password:
scribble@Scribble:~$ sudo mount /dev/sda1 /media/usb -o umask=000
mount: special device /dev/sda1 does not exist

then I tried adding a line to fstab....

/dev/sda1 /mount/point vfat iocharset=utf8,umask=000,uid=1000,gid=1000,auto,rw ,nouser 0 0# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f81bae6f-78e8-482f-9672-821db8a5baf5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=3DA7-3DAF  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=17e47e15-7e54-4faf-8104-460791a9f508 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


Any suggestions?  Thanks a lot by the way.

---

### Post by Azakus on 2006-12-23
{trying to delete this}

---

### Post by bodhi.zazen on 2006-12-23
> **dasuberdog said:**
> Any suggestions?  Thanks a lot by the way.

Since we are having  problems, can you post the output of:```
sudo fdisk -l
```

And```
cat /etc/fstab
```

Also, is the disk formatted ?

---

### Post by trav5 on 2006-12-25
I am also having this same problem. ```
tux@tux-laptop:~$ sudo fdisk -l

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1065     8554581    c  W95 FAT32 (LBA)
/dev/hda2            1066        2301     9928170   83  Linux
/dev/hda3            2302        2432     1052257+  82  Linux swap / Solaris

``````
tux@tux-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=4d15efec-3681-429b-b3c6-7eb6fc98fd74 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=302F-9A85  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=966509b3-d8a9-41eb-8909-4b766306b56d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

``` This was a ntfs drive. I used gparted to format to fat 32. It mounted after I formated and I copied a lot of music to it. It showed up as /dev/sda1. I am also not able mount on my win2k fat 32 partition but that seems to be a driver problem. It will mount on my sisters xp ntfs box. Thanks for any help.

---

### Post by grantm on 2006-12-25
Hi there,

I formatted my external hard drive with fat32 and here was what I typed in the terminal and here is what happened.


grant@grant-desktop:~$ cd /media/usbdisk

grant@grant-desktop:/media/usbdisk$ sudo su
password:*********

root@grant-desktop:/media/usbdisk# chown -R root:grant /media/usbdisk

root@grant-desktop:/media/usbdisk# chmod g+w /media/usbdisk
root@grant-desktop:/media/usbdisk# exit
grant@grant-desktop:/media/usbdisk$

I did nothing more, nothing less
good luck!
Grant

and yes your external drive is also referred to as </dev/sda1>

---

### Post by grantm on 2006-12-26
Sorry unclear language.

what I meant to say was here was what I typed into the terminal to get the permissions working.

hope it works

Grant

---

### Post by dasuberdog on 2007-01-06
Sorry it took me so long to get back to this.  I  set up my external hard drive then I went to Mexico for two weeks.

Ok here is my "sudo fdisk -l"

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1144     9189148+  83  Linux
/dev/hda2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/hda3            1145        1275     1052257+  82  Linux swap / Solaris
/dev/hda5            1276        9728    67898691    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    b  W95 FAT32

Disk /dev/sdb: 262 MB, 262144000 bytes
16 heads, 32 sectors/track, 1000 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1000      255975+   4  FAT16 <32M

```

I really don't understand this part of it.  

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    b  W95 FAT32

Disk /dev/sdb: 262 MB, 262144000 bytes
16 heads, 32 sectors/track, 1000 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1000      255975+   4  FAT16 <32M
```

I don't understand the last thing /dev/sdb1 starts at 1 and ends at 1000.  Seems like there would just ba a 320 gig w95 fat 32 partition in sda1. 


And here is my "cat /etc/fstab"

```
scribble@Scribble:~$ cat /etc/fstab
/dev/sda1 /mount/point vfat iocharset=utf8,umask=000,uid=1000,gid=1000,auto,rw ,nouser 0 0# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f81bae6f-78e8-482f-9672-821db8a5baf5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=3DA7-3DAF  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=17e47e15-7e54-4faf-8104-460791a9f508 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
scribble@Scribble:~$ 
```

I really don't understand,  "cat /etc/fstab"  All of that is gibberish to me.  I've kind of messed around reading about it but a light bulb hasn't gone off yet.  If anyone could simplify it for me it would be appreciated.

I used the Ubuntu 6.10 install to format the external drive fat 32.  Should be formatted just fine except for the above mentioned confusion

Thanks for all the help and I hope someone is still paying attention after two weeks.

Scribble

---

### Post by brolin on 2007-01-06
> **grantm said:**
> 
grant@grant-desktop:~$ cd /media/usbdisk

grant@grant-desktop:/media/usbdisk$ sudo su
password:*********

root@grant-desktop:/media/usbdisk# chown -R root:grant /media/usbdisk

root@grant-desktop:/media/usbdisk# chmod g+w /media/usbdisk
root@grant-desktop:/media/usbdisk# exit
grant@grant-desktop:/media/usbdisk$


This is unnecessary.  Use something like this in your /etc/fstab:

```
UUID=6487-96B3          /mnt/flash_drive        vfat    noauto,owner,uid=brolin,gid=users,umask=077,shortname=winnt 0 0
```

This makes all files in my vfat file system owned by brolin:users with mode 0700.

---

### Post by dasuberdog on 2007-01-07
bump

---

### Post by bodhi.zazen on 2007-01-07
[how to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

### Post by dasuberdog on 2007-01-07
I think something is broken or I just don't know what I'm doing.  Everytime I try and do what the fstab link says to do I get a command not found or line is broken in fstab...etc etc...  At this point I'm wondering if it would be easier to take this drive back and get another.

---

### Post by dasuberdog on 2007-01-07
```
scribble@Scribble:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1144     9189148+  83  Linux
/dev/hda2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/hda3            1145        1275     1052257+  82  Linux swap / Solaris
/dev/hda5            1276        9728    67898691    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    b  W95 FAT32
scribble@Scribble:~$ 

```





```
scribble@Scribble:~$ cat /etc/fstab
/dev/sda1 /mount/point vfat iocharset=utf8,umask=000,uid=1000,gid=1000,auto,rw ,nouser 0 0# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f81bae6f-78e8-482f-9672-821db8a5baf5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=3DA7-3DAF  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=17e47e15-7e54-4faf-8104-460791a9f508 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
scribble@Scribble:~$ 


```

Can anyone see anything wrong with either of those???

I get this when I try to mount the drive sda1 which is labeled Celia

```
scribble@Scribble:~$ mount celia
[mntent]: line 1 in /etc/fstab is bad
mount: can't find celia in /etc/fstab or /etc/mtab
```

---

### Post by dasuberdog on 2007-01-07
Got it working.  Thanks for the help.

---

