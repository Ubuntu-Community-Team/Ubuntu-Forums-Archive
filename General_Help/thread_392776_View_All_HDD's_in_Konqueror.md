---
title: "View All HDD's in Konqueror"
date: 2007-03-24
forum: General Help
---

### Post by Imsati on 2007-03-24
As of right now, I can only see my three XP partitions when I open 'Storage Media', listed as sda1/5/6. How do I gain control to change the name of them to something else, specifically 'XP OS', 'XP Software', and 'Jason'?

Also, why can I not see my Root and Home drives under Storage Media? I can see both optical drives and my floppy, but neither of my Kubuntu HDDs. I would also like to change the names from sdb(whatever partition) to Root and Home. I'm just an organization-freak like that :)

Not sure if this helps any, but...

jason@JasonK:~$ sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1958    15727603+   7  HPFS/NTFS
/dev/sda2            1959        9963    64300162+   f  W95 Ext'd (LBA)
/dev/sda5            1959        3916    15727603+   7  HPFS/NTFS
/dev/sda6            3917        9963    48572496    7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         243     1951866   82  Linux swap / Solaris
/dev/sdb2   *         244        2067    14651280   83  Linux
/dev/sdb3            2068        5106    24410767+  83  Linux

and...

jason@JasonK:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb3       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Thanks so much!
--Jay (eagerly awaiting the day he can drop MS forever)

---

### Post by mexlinux on 2007-03-25
First go to: systemsettings - Advanced - System Management - Disks and Filesystems 
There switch to Administrator Mode and then mount as you wish and enable the partitions you want.
Hope that helps.

---

### Post by Imsati on 2007-03-25
When I try to open Admin Mode, I see the red border, but then nothing. No password prompt, and no info inside the red border to change.

---

### Post by scxtt on 2007-03-25
try **kdesu systemsettings** ...

---

### Post by Imsati on 2007-03-25
Results:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

---

### Post by mexlinux on 2007-03-27
> **Imsati said:**
> When I try to open Admin Mode, I see the red border, but then nothing. No password prompt, and no info inside the red border to change.

Try inconsole:
```
sudo -k
```
Then go to systemsettings

---

