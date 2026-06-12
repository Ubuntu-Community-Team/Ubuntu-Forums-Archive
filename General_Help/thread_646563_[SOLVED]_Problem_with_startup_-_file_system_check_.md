---
title: "[SOLVED] Problem with startup - file system check fails"
date: 2007-12-21
forum: General Help
---

### Post by dorkdork777 on 2007-12-21
After deleting my Kubuntu partition, and resizing my other partitions to give them more space to breathe, I had a few problems, all GRUB related. The Super Grub Disc I burnt a few months got rid of the first error, and booting into my Ubuntu 7.10 LiveCD and toying with my menu.lst let me boot into my Ubuntu installation. So all is well and good - mostly.

I just have one problem - during the Ubuntu boot process, before the bar gets full of orange, the icon and bar are replaced by a terminal, displaying the following - 

> *Checking root filesystem...
fsck 1.40.2 (12-Jul-2007)
/dev/sda5: clean, 147548/3981312 files, 2715096/7936110 blocks    [OK]
*Checking file systems
fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=d36719b0-970d-4c01-a675-f3d42ab0d41f'
fsck died with exit status 8
*File system check failed
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair file systems manually.
*A maintenance shell will now be started.


From the "maintenance shell" I can type 'exit' to bring me to the graphical login screen, and everything is as it should be from there.

The log the terminal referenced is this:

> Log of fsck -C -R -A -a 
Fri Dec 21 15:49:38 2007

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=d36719b0-790d-4c01-a675-f3d42ab0d41f'

fsck died with exit status 8

Fri Dec 21 15:49:38 2007
----------------

What I would like to know is this - 

1. How do I stop it going into the terminal?
2. What, exactly, is the text from the terminal saying? Is it warning me of corruption, or... what?

Thanks a lot for your help!

---

### Post by cdenley on 2007-12-21
It looks like you have an entry in /etc/fstab for a partition which no longer exists. Post this output if you don't know what changes to make.

```

ls -l /dev/disk/by-uuid
cat /etc/fstab
sudo fdisk -l

```

---

### Post by dorkdork777 on 2007-12-21
OK, thanks a lot for your reply!

> 
 ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2007-12-21 15:49 3F163DDB5D65D7E9 -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-12-21 15:49 690ebf12-ea40-55a5-de64-447a78c63e30 -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-12-21 15:49 a40b4f0a-585b-437f-adc3-c79a41a77901 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-12-21 15:49 F23018C530189329 -> ../../sda1

> 
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a40b4f0a-585b-437f-adc3-c79a41a77901 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=F23018C530189329 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=3F163DDB5D65D7E9 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=d36719b0-790d-4c01-a675-f3d42ab0d41f /media/sda5     ext3    defaults        0       2
# /dev/sda2
UUID=690ebf12-ea40-55a5-de64-447a78c63e30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

> 
sudo fdisk -l
[sudo] password for chris:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x493936ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9891    79449426    7  HPFS/NTFS
/dev/sda2           30275       30401     1020127+  82  Linux swap / Solaris
/dev/sda3            9892       26321   131973975    7  HPFS/NTFS
/dev/sda4           26322       30274    31752472+   5  Extended
/dev/sda5           26323       30274    31744440   83  Linux

Partition table entries are not in disk order


Any help from that?



EDIT: Here's my /etc/fstab, if it helps - 
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a40b4f0a-585b-437f-adc3-c79a41a77901 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=F23018C530189329 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=3F163DDB5D65D7E9 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=d36719b0-790d-4c01-a675-f3d42ab0d41f /media/sda5     ext3    defaults        0       2
# /dev/sda2
UUID=690ebf12-ea40-55a5-de64-447a78c63e30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

sda6 is the partition that I deleted.

---

### Post by dorkdork777 on 2007-12-21
Bump

---

### Post by cdenley on 2007-12-21
"sudo gedit /etc/fstab"

Delete or insert a # before the line:
"UUID=d36719b0-790d-4c01-a675-f3d42ab0d41f /media/sda5 ext3 defaults 0 2".

You error says that the UUID d36719b0-790d-4c01-a675-f3d42ab0d41f does not exist. This is confirmed by the output you of "ls -l /dev/disk/by-uuid" that you posted. However, you have a line for that UUID in fstab. Remove that line, and the problem should go away.

---

### Post by dorkdork777 on 2007-12-21
Commented out the line, and restarted - now the boot process runs by as normal. Thank you so much! :D

---

