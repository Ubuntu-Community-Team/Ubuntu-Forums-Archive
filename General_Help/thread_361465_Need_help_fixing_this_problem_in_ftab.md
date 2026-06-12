---
title: "Need help fixing this problem in ftab"
date: 2007-02-14
forum: General Help
---

### Post by maddbaron on 2007-02-14
*Fstab*

added two lines so my external HD can work saved. Did sudo mount -a and got this error back
> sudo mount -a
[mntent]: warning: no final newline at the end of /etc/fstab
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



This is how my fstab looks now:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=531a5675-91ee-4198-ade2-3be117831552 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=3007-17F2  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=320D-180E  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=58a4511c-0605-4c1f-aa9c-b414a989d447 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1 /media/sda1 vfat defaults,umask=0 0 0
/dev/sda5  /media/sda5  vfat  defaults,umask=0 0 0

Did I place the final two lines in the wrong place?

---

### Post by WW on 2007-02-14
For the first error message, edit /etc/fstab, go to the end of the last line in the file, hit enter (i.e. add a final newline), and save it.  (The error message is self-explanatory.)

For the second error message: Are you sure the filesystem on your external drive is vfat?  Try mounting it in a terminal with this command
> $ sudo mount -t vfat  /dev/sda1 /media/sda1
If that doesn't work, try
> $ sudo mount -t auto /dev/sda1 /media/sda1
and see if **mount** can figure out the type automatically.

---

### Post by maddbaron on 2007-02-14
> **WW said:**
> For the first error message, edit /etc/fstab, go to the end of the last line in the file, hit enter (i.e. add a final newline), and save it.  (The error message is self-explanatory.)

For the second error message: Are you sure the filesystem on your external drive is vfat?  Try mounting it in a terminal with this command

If that doesn't work, try

and see if **mount** can figure out the type automatically.

I hit enter at the end of the last line and still got the error 
I made the external fat32, I did not see the vfat option I assumed they were the same thing but now I guess not.
I entered the two commends you stated and got an error for both saying command not found.
 I don't even know how my external is working all I did was enter mkdir and sda1 and sda5 and the thing started allowing me to save to it . Only problem is I can't for example if I have a rar file on my desktop extra to the external from the desktop . 
in fstab there is no UUID for the external HD either.
I don't know how its working now but I think I'll leave it alone, is adding sda1 and 5 to fstab important?

---

### Post by maddbaron on 2007-02-14
problem solved.

---

