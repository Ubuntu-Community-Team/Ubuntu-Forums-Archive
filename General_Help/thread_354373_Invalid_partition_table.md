---
title: "Invalid partition table"
date: 2007-02-05
forum: General Help
---

### Post by lakelovers on 2007-02-05
I installed a second drive and have be unable to get it partitioned and mounted correctly. 
Gparted shows the drive with a single partition which is what I want but the drive is not mounted. I've tried numerous times to mount the drive but I'm doing something wrong because it never mounts. This is what I get with sudo fdisk -l /dev/hdb:
Disk /dev/hdb: 6448 MB, 6448619520 bytes
15 heads, 63 sectors/track, 13328 cylinders
Units = cylinders of 945 * 512 = 483840 bytes
[B]Disk /dev/hdb doesn't contain a valid partition table
[/B]

And this is my fstab setup:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1	/db 		ext3	defaults	1	1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0

When I try to mount the drive I get the message that the file type is not specified, but I don't see file types ID'd in instructions on mounting. I've read the man pages but still don't understand the syntax for the command line to mount the drive. I'd appreciate any suggestions or how-to's you can give me.

I'm thinking about formating the drive and starting over. Is this a good idea or not?
Jerry

---

### Post by comfurtn on 2007-02-05
First, have you created the directory where you want to mount /dev/hdb?

> sudo mkdir /db

Second, the mount command you need to use is 
> sudo mount -a

If this returns any error messages, post them so I can help you further.

---

### Post by lakelovers on 2007-02-06
Thanks for your reply. Here's what I got using both commands:

jerry@Desktop:~$ sudo mkdir /db
Password:
mkdir: cannot create directory `/db': File exists
jerry@Desktop:~$ sudo mount -a
mount: special device /dev/hdb1 does not exist

Gparted shows /dev/hdba  ext3  6.01 GB

What do you suggest?

Jerry

---

### Post by comfurtn on 2007-02-06
> **lakelovers said:**
> Thanks for your reply. Here's what I got using both commands:

jerry@Desktop:~$ sudo mkdir /db
Password:
mkdir: cannot create directory `/db': File exists
jerry@Desktop:~$ sudo mount -a
mount: special device /dev/hdb1 does not exist

Gparted shows /dev/hdba  ext3  6.01 GB

What do you suggest?

Jerry

Okay, so your mount point exists, but it looks like we are trying to mount the wrong device.  What's the output of this command?
```
sudo fdisk -l
```

---

### Post by lakelovers on 2007-02-06
Here the output of sudo fdisk -l.
Perhaps the problem is in the last line "doesn't contain a valid partition table." 
Was I supposed to format the disk first? I didn't format it. By the way there is no data on that disk, yet.

Disk /dev/hda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3582    28772383+  83  Linux
/dev/hda2            3583        3738     1253070    5  Extended
/dev/hda5            3583        3738     1253038+  82  Linux swap / Solaris

Disk /dev/hdb: 6448 MB, 6448619520 bytes
15 heads, 63 sectors/track, 13328 cylinders
Units = cylinders of 945 * 512 = 483840 bytes

Disk /dev/hdb doesn't contain a valid partition table

---

### Post by comfurtn on 2007-02-06
If you have not yet formatted the disk, then you need to do so.  Install "gparted" using synaptic if you need a user-friendly partitioning tool.

---

### Post by lakelovers on 2007-02-06
I formated the drive, added a label (msdos), applied a new primary partition (full disk), then I tried mounting: "mount -a." And I got "Disk /dev/hdb doesn't contain a valid partition table." This thing is driving me whacko. Hopefully, you can get me through this.  I didn't leave any free space. Should I have done that to leave room for the partition table? Guess I'll try that but I don't know how much to leave, Probably not much. -Jerry

---

### Post by comfurtn on 2007-02-06
> **lakelovers said:**
> I formated the drive, added a label (msdos), applied a new primary partition (full disk), then I tried mounting: "mount -a." And I got "Disk /dev/hdb doesn't contain a valid partition table." This thing is driving me whacko. Hopefully, you can get me through this.  I didn't leave any free space. Should I have done that to leave room for the partition table? Guess I'll try that but I don't know how much to leave, Probably not much. -Jerry

Sorry we haven't resolved this yet, but I'll keep trying!  -_-
If you have formatted the disk, then the partition table exists.  What did you use to do the formatting?  AND, what is now the output of 
```
sudo fdisk -l
```??

Do you know which filesystem you formatted the drive to (i.e. ext3, fat32, ntfs, etc...)?  I would reccommend using GParted if you are not already, as it can sense most problems you could encounter when setting the disk up correctly.

---

### Post by lakelovers on 2007-02-06
I think I got it. I formated to ext3, and repartitioned leaving 2mb free (don't know whether that was necessary). I did this with gparted. Then in the terminal I used "sudo fdisk -a" and it mounted. I formated and repartitioned a couple of time and got an error message that was not specific but said that some opertions could be effected.The last time I didn't format but applied a msdos label, then partitioned and there was no error. As you already know this is a small drive which I'm using as backup. I don't know if the drive size is adquate but I don't have a lot of photo or music files. Thank you much for your help. If anything below looks out of order let me know.  Jerry

Disk /dev/hda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3582    28772383+  83  Linux
/dev/hda2            3583        3738     1253070    5  Extended
/dev/hda5            3583        3738     1253038+  82  Linux swap / Solaris

Disk /dev/hdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         784     6297448+  83  Linux

---

### Post by comfurtn on 2007-02-06
> **lakelovers said:**
> 
Disk /dev/hdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         784     6297448+  83  Linux


It all looks good ;) ... just make sure you mount it now as ext3 filesystem if you use the fstab entry.  Cheers.

---

