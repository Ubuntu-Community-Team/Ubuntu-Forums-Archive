---
title: "invalid mount options message on a windows cd"
date: 2008-04-14
forum: General Help
---

### Post by larryfroot on 2008-04-14
Hi,  I have tried to find a solution in the other threads that gave out this problem with no success, so I am running this one by the forum...I would be well grateful for any help at all.

I'm running Ubuntu Gutsy, attempting to get cdrom0 to open up to wine (its an exe file I am after)....the message arrives -  "Invalid mount option when attempting to mount the volume"  

Ok...I entered blkid

xxxxxxx@xxxxxxxxx:~$ blkid
/dev/sda1: UUID="cd1e001f-684e-4a3d-9ff3-41e88a13ed37" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="c6846a7c-35db-4c0f-af06-80a886dda4f0" 
/dev/sdb1: SEC_TYPE="msdos" UUID="4CB8-1D52" TYPE="vfat" 

Armed with that information I attempted to add the info from my misbehaving disk to the end of my fstab as:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cd1e001f-684e-4a3d-9ff3-41e88a13ed37 /               ext3    
/dev/sda1	/ ext3	defaults,user_xattr,errors=remount-ro 0
defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c6846a7c-35db-4c0f-af06-80a886dda4f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
#/dev/sdb1     
UUID=4CB8-1D52/media/sdb1 vfat defaults 0 2

So then I tried...again on the end of fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cd1e001f-684e-4a3d-9ff3-41e88a13ed37 /               ext3    
/dev/sda1	/ ext3	defaults,user_xattr,errors=remount-ro 0
defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c6846a7c-35db-4c0f-af06-80a886dda4f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1	/media/cdrom0	vfat	rw,user,noauto,exec 0	    0

And so 'dsmeg | tail' gave 

xxxxxxxxx@xxxxxxxx:~$ dmesg | tail  
[   69.399532] eth0: no IPv6 routers present
[  564.566003] UDF-fs: No partition found (1)
[  564.678011] Unable to identify CD-ROM format.
[ 1039.918627] UDF-fs: No partition found (1)
[ 1040.225002] Unable to identify CD-ROM format.
[ 1055.956340] UDF-fs: No partition found (1)
[ 1056.192535] Unable to identify CD-ROM format.
[ 1056.193167] Unable to identify CD-ROM format.
[ 1150.737504] UDF-fs: No partition found (1)
[ 1150.839256] Unable to identify CD-ROM format.

tried changing 'vfat' to 'vfat16' zilch. A bit depressing.

Where am I going wrong? 

Big thanks to anyone who can help me out of this hole!

---

### Post by pyrocajun2707 on 2008-04-14
Have you tried restarting with the cd still in the drive. It usually works for me when I log back in.

As for what causes it, I have no idea, but it sure is annoying.

Update: Try going to Computer and mount the drive manually. I've found that also works.

---

