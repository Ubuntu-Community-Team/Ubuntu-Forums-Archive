---
title: "Boot hangs on &quot;Checking Filesystems&quot;"
date: 2007-01-15
forum: General Help
---

### Post by Muchacho_Gasolino on 2007-01-15
When my system is booting up, it hangs for a minute or two on "Checking Root Filesystem" and then again on "Checking Filesystems". Each time before it hangs, it prints 
"fsck 1.39 (May 29 2006)" 
, or something very similar to that. Under "Checking Filesystems", it seems to check one system using fsck and then two others using dosfsck. It doesn't seem to hang when using dosfsck. I mount an ext3 root partition, a swap partition, an internal partition formatted in FAT32, and an external USB hard drive formatted in FAT32. I am pretty sure that the two FAT partitions are the partitions checked by dosfsck because of the device names listed. No device names are listed for the filesystems checked by fsck. 
Anyone know how to speed this up? Ubuntu blazes through everything else but gets stuck on these. Everything else takes about 30 seconds total to boot up.

---

### Post by Muchacho_Gasolino on 2007-01-28
Anybody have any suggestions?

---

### Post by luis.torres.gomez on 2007-03-19
you can boot from the livecd and from the console run fsck for the partition halted

---

### Post by mcduck on 2007-03-19
There's probably something wrong in your fstab file.. Could you post outputs of 'sudo fdisk -l' and 'cat /etc/fstab' here?

---

### Post by Muchacho_Gasolino on 2007-08-10
Sorry to drag up an old thread. Hopefully someone can still help me out.

```
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3502    28123168+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3503        5413    15350107+  83  Linux
/dev/sda3            5414        8762    26900842+   5  Extended
/dev/sda4            8763        9729     7764120   1c  Hidden W95 FAT32 (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5            5606        8762    25358571    b  W95 FAT32
/dev/sda6            5414        5605     1542177   82  Linux swap / Solaris

Partition table entries are not in disk order

```

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=fcbdec17-a5b0-4318-8455-2ec7363389a7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C2D4BAC0D4BAB64F /media/windoze     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=2A6D-11E8  /media/ibmrepair     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=44D2-02A7  /media/mobile     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=ee271b3d-f554-4b6d-9520-7fe519dbd20f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by mcduck on 2007-08-10
Running fsck on Windows filesystems (FAT & NTFS) seems to cause some problems in many cases (and IMHO it's pretty useless anyway). Open the fstab file for editing (hit Alt-F2 and run "gksudo gedit /etc/fstab") and change the last number on windows partition's entry lines from "1" to" 0"
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=fcbdec17-a5b0-4318-8455-2ec7363389a7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C2D4BAC0D4BAB64F /media/windoze     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/sda4
UUID=2A6D-11E8  /media/ibmrepair     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda5
UUID=44D2-02A7  /media/mobile     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda6
UUID=ee271b3d-f554-4b6d-9520-7fe519dbd20f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
After that save, and reboot, and your problem should be gone. :)

"1" should only be used for root parition, for other partitions you should use "2" (to check them after root) ot "0" (to disable fsck on that partition).

---

### Post by Muchacho_Gasolino on 2007-08-10
Thanks a lot mcduck! My computer starts up like a damn racehorse now.

---

### Post by mscir on 2007-12-19
Thank You mcduck,

I dual booted win98se adn ubuntu7.10 and was having the same problem for almost 2 minutes, I made the changes you specified and my ubuntu boots like a freaking "racehorse" now too. 

Best,
Mike

---

### Post by thoffland on 2007-12-21
Thank you from me too! I had the same problem with FSCK but it was not due to my Vista HDD it was my internal storage HDD.

---

### Post by Chris Musampa on 2008-03-03
I had the slow boot problem in 7.10 too, it would stop at this point for over a minute:
[http://i31.tinypic.com/2guy5ua.jpg]("http://i31.tinypic.com/2guy5ua.jpg")

mcduck's advice has sorted the slow Ubuntu boot but I think the underlying cause still exists.


The following was my install sequence:

Empty drive D: and remove its logical partition using WinXP disk management utility.
Boot from the Ubuntu CD and double click install.
Select manual partitioning. 
Add1024MB swap partition @end of free space
Added ext3 partition in remaining free space with / as the mount point
Let Ubuntu install

As well as the slow Ubuntu boot I noticed XP was running at a crawl due to monitor.exe hogging resources, coincidentally (or not) google reveals that monitor.exe is a part of Acer erecovery and was probably stuck trying to check the recovery partition. Killing off the monitor.exe process gets XP back up to speed.

It looks like the Ubuntu partitioner has buggered my hidden recovery partition even though I deliberately left it untouched at setup time, does anyone know if this recoverable?

---

### Post by Vencislago on 2008-03-26
Thanks mcduck,
:popcorn:

I was experiencing this problem for a while and finally I found the answer.
Don't know if this is the right way to do it but, it works.
 :guitar:

---

