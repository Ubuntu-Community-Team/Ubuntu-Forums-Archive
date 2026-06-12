---
title: "fat32 read/write and preserving file info (feisty)"
date: 2007-09-26
forum: General Help
---

### Post by shelie on 2007-09-26
So here's my tale of woe and minor frustration:
Dapper went belly-up on me a few weeks ago.  I'd been hoping to hold out until Gutsy in Oct, but my hand was forced when the box just froze up and I decided to pop in knoppix and get onto Feisty, via a good cleaning with gparted.  This was a good move, overall.  BUT.  This little niggle has emerged.

In Dapper, I would connect my camera via USB, and using Nautilus I would copy/cut and paste the photos into a new directory in my images folder (on hda6, see below).  No problem.

Since the move to Feisty, while the most important function of saving the files still works (thank goodness), the file date/time is not preserved.  This is incredibly frustrating, as I prefer to use the file info to sort my photos in directories easily, without having to check the EXIF data for when the photo was originally taken.

Some kindly geek friends online suggested I use cp -p in the terminal to work around this.  But with no joy: I was informed that the "operation not permitted".  The files will copy, but they still lose the time/data info - saving instead with the time/date at save point.

I've been googling/searching the forums quite a bit about this.  Having trouble finding a solution that makes any sense to my somewhat inexperienced brain :\

I'm pretty sure it's a problem with how my fat32 partitions are mounting.  Doesn't matter if I'm moving the files on the same physical disk or to a different disk, they all show the same behaviour.

It worked in Dapper, why is it not working in Feisty?? :(

Here is my current fstab, which I have not touched one iota since installing Feisty:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda8
UUID=38d8e6a7-127b-4cb4-9743-ec592b524fac /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7
UUID=412af099-e5ce-4837-b559-706880ba4f12 /home           ext3    defaults        0       2
# /dev/hda1
UUID=B290CAA290CA6D03 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=0407-0D28  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=40F7-A66C  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdd1
UUID=4659-2722  /media/hdd1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=99e32f14-254d-4e66-a8fb-6225e576f590 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
Notes: 
hda1 is NTFS windows 2000 partition which I don't touch within ubuntu because I have no need to.
hda6 is my primary shared file area, fat32, on the same physical disk as the ext3 partitions and win2k
hdb1 and hdd1 are two separate disk, both fat32 for sharing

And to pre-empt one suggestion: after reading a fair bit about NTFS vs fat and the good read/write support ntfs does now have, I AM considering shuffling everything around and switching to ntfs on the shared drives/partitions.  BUT I really don't have time to fuss with that process for about 4 months!  So I need to find a fix for the file info preservation issue - especially since it all worked FINE in Dapper! *sigh*

EDIT: also...
the ownership of the fat32 drives is all root/plugdev (wtf is the group plugdev??)

su to root and attempting the cp -p command gave the same result: not permitted.  I also tried a chown on the destination folder for the photos, as root, and was also told I didn't have permission.  Bleh.

---

### Post by shelie on 2007-10-12
I fixed this by adding uid=1000 (and changing gid to 1000) in fstab for all the vfat volumes I have - as described here: [http://kerneltrap.org/node/7080]("http://kerneltrap.org/node/7080")

---

### Post by ryke on 2007-11-18
hi, I have the same problem, too. I have spent a lot of time in google, but I am not able to find how to solve it :(

I've found this thread, and I'v tried to modify the fstab file, adding uid=1000 and gid=1000, uid=1000 but it doesn't work for me (I do the following: modify fstab, sudo mount -a, and try to copy from Terminal using parameter -p... and I get the message "... operation not permitted").

I'm using Gutsy.

I doesn't work in Fat32 nor NTFS. However, it works in several USB drivers, with FAT32 and NTFS partitions, so I think that is not a problem due to the partition type, doesn't it ?

Any help?

Thanx in advance

---

### Post by ryke on 2007-11-18
hi, I have the same problem, too. I have spent a lot of time in google, but I am not able to find how to solve it :(

I've found this thread, and I'v tried to modify the fstab file, adding uid=1000 and gid=1000, uid=1000 but it doesn't work for me (I do the following: modify fstab, sudo mount -a, and try to copy from Terminal using parameter -p... and I get the message "... operation not permitted").

I'm using Gutsy.

I doesn't work in Fat32 nor NTFS. However, it works in several USB drivers, with FAT32 and NTFS partitions, so I think that is not a problem due to the partition type, doesn't it ?

Any help?

Thanx in advance

---

### Post by ryke on 2007-11-19
Hi,

I find here the solution... it works :-)

[http://yoonkit.blogspot.com/2007/09/preserving-time-stamps-on-fat32-copies.html](http://yoonkit.blogspot.com/2007/09/preserving-time-stamps-on-fat32-copies.html)

Regards

---

