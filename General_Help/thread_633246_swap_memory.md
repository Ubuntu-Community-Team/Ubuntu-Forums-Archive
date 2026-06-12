---
title: "swap memory"
date: 2007-12-06
forum: General Help
---

### Post by nate_nightroad on 2007-12-06
i've been using ubuntu for quite some time and i used to not have any swap memory for my ubuntu,so today i create a swap memory for it...but everytime when i boot up,that swap memory dint not mount automatically....is there anyway to make it auto?

---

### Post by bingoUV on 2007-12-06
1. How did you create swap memory for your ubuntu?
2. Why do you think it is not mounted?
3. Output of the command 
```

/sbin/swapon -s

```

---

### Post by nate_nightroad on 2007-12-06
i use windows(acronis) to resize ubuntu partition for swap...then i login back to ubuntu and use gparted to create the swap...i restart after tat then i use gparted to check to see if swap is mounted,but it aint...i have to right click tat swap partition and select swapon

---

### Post by rsambuca on 2007-12-06
You have to add the swap entry to your fstab to have it automounted at boot.

---

### Post by nate_nightroad on 2007-12-06
i know i gotta add the entry into my fstab bur i dunno how...any help?

---

### Post by rsambuca on 2007-12-06
Post the output of the following three commands:

sudo fdisk -l

cat /etc/fstab

blkid

---

### Post by atlfalcons866 on 2007-12-06
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by nate_nightroad on 2007-12-07
for fdisk:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x588aff1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6486    52098763+   7  HPFS/NTFS
/dev/sda2           18936       19457     4192965    5  Extended
/dev/sda3           12451       18935    52090761+  83  Linux
/dev/sda5           18936       19457     4192933+  82  Linux swap / Solaris

for fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4c237676-f2e9-49-Ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4c237676-f2e9-4993-98ec-2613b23e188e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=4697-91A3  /media/sdc5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
93-98ec-2613b23e188e /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0

for blkid:
/dev/sda1: TYPE="ntfs" 
/dev/sda3: UUID="4c237676-f2e9-4993-98ec-2613b23e188e" SEC_TYPE="ext2" TYPE="ext3"

note tat i already swapon the swap partition...

---

### Post by i586 on 2007-12-07
Edit your **/etc/fstab** file by adding the following line:

```

/dev/sda5 none swap sw 0 0

```

The above piece of code will automatically mount your **swap** partition at startup.

Regards.

---

### Post by rsambuca on 2007-12-07
> **nate_nightroad said:**
> for fdisk:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x588aff1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6486    52098763+   7  HPFS/NTFS
/dev/sda2           18936       19457     4192965    5  Extended
/dev/sda3           12451       18935    52090761+  83  Linux
/dev/sda5           18936       19457     4192933+  82  Linux swap / Solaris

for fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4c237676-f2e9-49-Ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4c237676-f2e9-4993-98ec-2613b23e188e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=4697-91A3  /media/sdc5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
93-98ec-2613b23e188e /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0

for blkid:
/dev/sda1: TYPE="ntfs" 
/dev/sda3: UUID="4c237676-f2e9-4993-98ec-2613b23e188e" SEC_TYPE="ext2" TYPE="ext3"

note tat i already swapon the swap partition...
You are missing the UUID info for the swap partition, but no matter.  You can open your fstab using gedit```
gksudo gedit /etc/fstab
```Add this line to the bottom, save the file, and it will automatically mount your swap when you boot.```
/dev/sda5    none            swap    sw              0       0
```

---

