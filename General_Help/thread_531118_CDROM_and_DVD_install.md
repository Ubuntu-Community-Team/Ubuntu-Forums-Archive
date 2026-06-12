---
title: "CDROM and DVD install"
date: 2007-08-21
forum: General Help
---

### Post by mikey5555 on 2007-08-21
I originally installed Ubuntu 7.04 with only 1 optical drive, cdrom, and would now like to add a Dvd-RW drive to my system.  I have physically installed the 2nd drive, DVD-RW, to the same IDE interface as the CDROM,  This would be the Sec IDE interface.  CDROM is jumpered to Master and DVD is jumpered as Slave.  HAL sees both drives as scd0 and scd1 respectively.  when I try to mount the DVD system says no entry found in fstab or mtab.  
What should the fstab entry be for the DVD-RW drive?  Do I need a link in the /dev directory for this and if so, could someone give me a pointer on how to create the link?  My fstab follows:

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=eaab1b24-6b26-4018-ba3c-10f30e52d1d5 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda5
UUID=19003608-8941-40ef-82f2-85afc9c7541d none            swap    sw            
  0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/md0        /media/raid     auto    defaults        0       10
[/B]

Regards....
mikey5555

---

### Post by manimal on 2007-08-21
/dev/cdrom is probably a symbolic link to an actual device file in your /dev/ directory.  You can see this by typing:
```
ls -al /dev/cdrom
```
In my case, the result of this command is:
```
lrwxrwxrwx 1 root root 3 2007-08-21 04:23 /dev/cdrom -> hdc
```
(in your case, it sounds like the output might have 'scd0' instead of 'hdc').  So, /dev/cdrom really just "points" to the file /dev/hdc, and people use the link, because it is much easier to remember and more general.  In any case, you could have the line:
```
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0 
```
in /etc/fstab, and it would still work.

So, there are two things you can do:

[LIST=1]
[*]Make a symbolk link to the new cd device.  In this case, you make a symbolic link using the command:
```
 sudo ln -s /dev/scd1 /dev/cdrom1
```
'ln' is a command for making links and the '-s' makes the link symbolic.  Check out the man page (man ln) for more info. Then add this line to /etc/fstab:
```
/dev/cdrom1 /media/cdrom1 udf,iso9660 user,noauto 0 0 
```
[*]Put the actual device name in /etc/fstab.  Just add this line to /etc/fstab:
```
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0 
```
[/LIST]

In both these cases, you need to make the directory '/media/cdrom1' and make sure it has the same permissions as '/media/cdrom0'.

---

