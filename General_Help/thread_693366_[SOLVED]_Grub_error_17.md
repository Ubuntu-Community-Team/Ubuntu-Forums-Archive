---
title: "[SOLVED] Grub error 17"
date: 2008-02-10
forum: General Help
---

### Post by bmeyer on 2008-02-10
Ubuntu recently crashed on my box and reset my BIOS to all of it's default settings.  After fixing all of that, grub gives me the Error 17.  I don't believe it's due to any settings in the BIOS, but it may be the issue.

I've been trying to fix my menu.lst and have not had any success.  I've also tried doing the root and setup in the grub prompt to no avail.  No USB drives or anything external is plugged in.  Any ideas?

/boot/grub/device.map:
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```

fdisk -l (sda--backup drive, sdb--ubuntu, sdc--windows):
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007655a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27cf27ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2432    19535008+  83  Linux
/dev/sdb2            2433        2675     1951897+  82  Linux swap / Solaris
/dev/sdb3            2676        9729    56661255   83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000015

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9728    78140128+   7  HPFS/NTFS
```


/boot/grub/menu.lst:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a867756d-4647-4b76-a6b2-f455ab44935b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a867756d-4647-4b76-a6b2-f455ab44935b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

---

### Post by bmeyer on 2008-02-11
Also, here is fstab and mtab -- is anything missing here?

/etc/fstab:
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb2 swap swap defaults 0 0
```

/etc/mtab:
```
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
/dev/scd0 /media/BF2\040CD\0401 iso9660 ro,nosuid,nodev,uid=999,utf8 0 0
```

---

### Post by HappyFeet on 2008-02-11
sda1, sdb1, sdb3 and sdc1 are missing from the fstab.

---

### Post by HappyFeet on 2008-02-11
before anything else, change the xp drive to (hd0,0) in /boot/grub/menu.lst:

---

### Post by bmeyer on 2008-02-11
> **HappyFeet said:**
> sda1, sdb1, sdb3 and sdc1 are missing from the fstab.

My fstab now contains the following.  The error 17 still occurs.
Thanks for the help thus far -- any more ideas?
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=a867756d-4647-4b76-a6b2-f455ab44935b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc1
UUID=F45C38C15C388082 /windows         ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb3
UUID=065e34c9-b47b-4bbc-b6c1-5392acec596d /home           ext3    defaults        0       2
# /dev/sda1
UUID=4691-219E  /backup     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=12d89b9c-12d3-487d-bc07-3f17a93e0c69 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by bmeyer on 2008-02-11
I re-ordered the drives in device.map so that the linux drive is hd0 and changed menu.lst to reflect that.  Everything works just fine now.  Not sure how the hell it broke ;)

Thanks for the help though...

---

