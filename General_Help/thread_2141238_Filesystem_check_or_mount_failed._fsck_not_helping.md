---
title: "Filesystem check or mount failed. fsck not helping"
date: 2013-05-02
forum: General Help
---

### Post by Celzo on 2013-05-02
Hi, 

For some reason, yesterday skype crashed with some I/O error and said to reinstall it. I did  that and then my PC restarted showing following error at start 

> **Filesystem check or mount failed.**
  **A maintenance shell will now be started.**
  **CONTROL-D will terminate this shell and continue booting after re-trying filesystems. Any further errors will be ignored.**

I ran fsck -f and it found few errors  and fixed them.  I tried hitting CONTRO-D then but everything I get immediately is the same message. 
I then tried reboot and shutdown commands but PC would just hang at "shutting down processes" or something like that.  If I reboot my PC over restart button I get the same message again.   

I booted from Live cd now and I can normally see my partitions and hard drivers.  
Here is the fdisk -l output. 

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x077de6f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   100358054    50178996    7  HPFS/NTFS/exFAT
/dev/sda2       100358055   312576704   106109325    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000402ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      499711      248832   83  Linux
/dev/sdb2          501758   156301311    77899777    5  Extended
/dev/sdb5          501760   156301311    77899776   8e  Linux LVM

Disk /dev/mapper/Voyager-root: 76.5 GB, 76546048000 bytes
255 heads, 63 sectors/track, 9306 cylinders, total 149504000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/Voyager-root doesn't contain a valid partition table

Disk /dev/mapper/Voyager-swap_1: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders, total 6291456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/Voyager-swap_1 doesn't contain a valid partition table



Here is the fstab output
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/Voyager-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=5826e790-9944-4817-9e9c-3b14bf502149 /boot           ext2    defaults        0       2
/dev/mapper/Voyager-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

and here is the blkid output 
> ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="Igre" UUID="1E2CFD042CFCD82B" TYPE="ntfs" 
/dev/sda2: LABEL="Storage" UUID="B84C13C44C137BF6" TYPE="ntfs" 
/dev/sdb1: UUID="5826e790-9944-4817-9e9c-3b14bf502149" TYPE="ext2" 
/dev/sdb5: UUID="2cgDDQ-CkWY-hAY9-ST3i-Su5m-bA1u-TDgWbf" TYPE="LVM2_member" 
/dev/sr0: LABEL="Ubuntu 13.04 i386" TYPE="iso9660" 
/dev/mapper/Voyager-root: UUID="c94261b0-82c6-4f2c-80c7-b53ba7c56680" TYPE="ext4" 
/dev/mapper/Voyager-swap_1: UUID="96870738-8c2f-4e37-a751-d30bd1212c15" TYPE="swap" 


Although I never touched fstab file.  From googling around, I saw that almost everyone fixed it with running fsck but for some reason it doesn't work for me.  Here are some images from disk utility on live cd. 
[http://www.pohrani.com/f/2o/Sv/Hh7PcEo/screenshot-from-2013-05-.png](http://www.pohrani.com/f/2o/Sv/Hh7PcEo/screenshot-from-2013-05-.png)
[http://www.pohrani.com/f/3m/vu/1C8mRSoY/screenshot-from-2013-05-.png](http://www.pohrani.com/f/3m/vu/1C8mRSoY/screenshot-from-2013-05-.png)
[http://www.pohrani.com/f/47/5Y/3lUGjfJf/screenshot-from-2013-05-.png](http://www.pohrani.com/f/47/5Y/3lUGjfJf/screenshot-from-2013-05-.png)
[http://www.pohrani.com/f/2G/KL/n8sVHuZ/screenshot-from-2013-05-.png](http://www.pohrani.com/f/2G/KL/n8sVHuZ/screenshot-from-2013-05-.png)

Also, everything is read only  wwheter I boot from live cd or try recovery console. 


I really don't understand what went wrong here.  I never ever had  problems like this... but it seems there's a first time for everything. And right  at the wrong moment since I have exam tomorrow and I need my PC today :/ 

p.s. 
I'm using latest version of kubuntu

---

