---
title: "reboot ruined something on NTFS drives"
date: 2008-01-17
forum: General Help
---

### Post by yurtos on 2008-01-17
hey folks, 

i rebooted my computer from Gutsy logon screen without login and tried to boot XP. i can see the windows XP logo, blue dots moving but when it suppose to show the windows Desktop screen stays black forever and nothing happens. i booted back to Ubuntu without problems but my NTFS mounted drives are gone. 

i saw this post:
[http://ubuntuforums.org/showthread.php?t=519329](http://ubuntuforums.org/showthread.php?t=519329)

but it does not help me as i can not boot the XP to shut it down properly. how can i get everything working without reinstalling windows?

here is my fdisk:
```

yurtos@ebuntu:~$ sudo fdisk -l
[sudo] password for yurtos:

Disk /dev/sda: 37.0 GB, 37019566080 bytes
111 heads, 17 sectors/track, 38316 cylinders
Units = cylinders of 1887 * 512 = 966144 bytes
Disk identifier: 0x69006900

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19645    18535049    7  HPFS/NTFS
/dev/sda2           37787       38316      500055   82  Linux swap / Solaris
/dev/sda3           19646       37785    17115090   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04cbcd49

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13991   112382676    7  HPFS/NTFS
/dev/sdb2           13992       24190    81923467+   f  W95 Ext'd (LBA)
/dev/sdb5           13992       24190    81923436    7  HPFS/NTFS

```

my fstab:
```
yurtos@ebuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c0d73263-0c32-4e62-b565-295da1646433 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=381C38791C3833EA /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=345818DF5818A1A2 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=2A188D1C188CE7E1 /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=e87d962e-2e5b-45e3-b256-6dec9546b898 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by logos34 on 2008-01-18
did you run checkdisk as recommended in the thread you posted?

Boot from the XP install CD, hit 'R' for Recovery Console and run

**chkdsk /r**

Or use ntfsfix from ubuntu to flag it 'dirty' (triggers chkdsk next boot):

**sudo apt-get install ntfsprogs**

**ntfsfix /dev/sda1** (or sdb1, not sure which it is)

---

### Post by yurtos on 2008-01-18
thank you for pointing out chkdsk part, 
after running "chkdsk /r" in recovery console i got NTFS drives working again but windows will not boot fully. i can see windows xp boot logo and blue dots whizzing but when screen changes instead of showing desktop (logon is automatic) it remains blank.

is there any way to fix XP loading issue?  

p.s. im glad that at least my Ubuntu is rock solid ;)

---

