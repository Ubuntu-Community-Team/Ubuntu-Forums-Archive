---
title: "Well, my external drive's not being mounted again."
date: 2007-09-08
forum: General Help
---

### Post by Casull on 2007-09-08
Right, let's do this.

So, this is my second install of Ubuntu, after I had to reformat the first one because it was also doing this.  Both times, my Dell Inspiron 6000 has a dual boot of Windows 2000 (games and whatnot) and Ubuntu 7.04.

Just today, the external hard drive, a SimpleTech SimpleDrive 150GB model seems to have stopped reading on my Ubuntu partition, just like last time.  What's more, the drive only reads on Windows 2000 now, and on Linux, the drive light blinks a very low light.  I can't figure out what exactly is up with this thing, and it seems that a reformat fixed it...but I don't want to reformat and reinstall Ubuntu every three months.

Well, obligatory terminal code:

```
x@x:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+   6  FAT16
/dev/sda2   *           9        1346    10747485    7  HPFS/NTFS
/dev/sda3            1347        6798    43793190    5  Extended
/dev/sda4            6799        7295     3992152+  db  CP/M / CTOS / ...
/dev/sda5            1347        1476     1044193+  82  Linux swap / Solaris
/dev/sda6   *        1477        6798    42748933+  83  Linux

Disk /dev/sdb: 2045 MB, 2045771776 bytes
128 heads, 32 sectors/track, 975 cylinders
Units = cylinders of 4096 * 512 = 2097152 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         976     1997636+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(975, 127, 32) logical=(975, 63, 32)

```
sdb1 is my PSP, for the record, not the drive.  Unfortunately.
```
x@x:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=d8ebee6b-d62c-412d-93f4-6d764700596a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D5-070D  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=10F4A688F4A67020 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda4       /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=f65df56b-acab-496d-a599-2e1305f3126a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```
```
x@x:~$ sudo cat /etc/mtab
/dev/sda6 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
/dev/sda1 /media/sda1 vfat rw,utf8,umask=007,gid=46 0 0
/dev/sda2 /media/sda2 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/sda4 /media/sda4 vfat rw,utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0

```
I'm at the end of my wits, again, and I'm about to just switch back to WIndows XP.  As much as I like Ubuntu, I can't have this repeating every three months.

Anything else I should include?

---

### Post by Casull on 2007-09-09
Hmm.  I think the error is in the bootup, as I see some text that just flies by; something about "hardware".  I've heard that the bootup log doesn't work exactly, so I ask if there's any way I can turn that quiet boot off so that I can read exactly what the hardware error is.

---

### Post by merlinus on 2007-09-09
Press e at grub menu, arrow down to the kernel line, press e and delete quiet and splash, press Enter, press b to boot.

---

