---
title: "Grub foiled by Windoze again!"
date: 2006-12-25
forum: General Help
---

### Post by sarc on 2006-12-25
I deleted the Windows98 partition (see Grub menu below) using WIndowsXP My Computer - manage - local disks.

This changed the MBR and I could not boot Edgy any more.

Ran Supergrub but it did not help.

Booted WinXP and recreated the partition with the same format and label.  No luck.

Ran the Edgy LiveCD and followed Forum advice to reinstall grub.  Nothing.

Grub insists that my root is in hd0,3, which it was when Edgy was booting happily.  Now however if I manually edit the Grub menu on boot and change root to hd0,1 I see the Ubuntu splash screen then the error 
/bin/sh: cant't access TTY
 Typing exit or ctrl-alt-f1 as suggested in the forum does nothing.

WinXP still boots.

The forum indicates that this error occurs when Ubuntu cannot find the root or swap files -  how do I tell it where they are? Supergrub and LiveCD are not doing the trick.  (And why did Windoze change them when I deleted the Win98 partition?).  I think if I start messing around by myself I'll dig myself in even deeper.


My menu.lst
```

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows 95/98/Me
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```


This is my current fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=ee8e1850-efef-48c8-a818-a5d69e1ac217 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=05B4B59970DDA36F /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=54AA-9C0B  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=1470-C70A  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=C41A-9E7B  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=349D-7DB0  /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=30e317ab-5535-4e15-a310-5316b9a2476c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

This is my current fdisk -l from LiveCD boot:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1960    15735667    7  HPFS/NTFS
/dev/sda2            1961        3871    15350107+  83  Linux
/dev/sda3            3872        4177     2457945    c  W95 FAT32 (LBA)
/dev/sda4            4178        9729    44596440    f  W95 Ext'd (LBA)
/dev/sda5            4178        6089    15358108+   b  W95 FAT32
/dev/sda6            6090        6395     2457913+  82  Linux swap / Solaris
/dev/sda7            6396        8001    12900163+   b  W95 FAT32
/dev/sda8            8002        9729    13880128+   b  W95 FAT32

```

HELP!  THANKS!

---

### Post by Vox754 on 2006-12-25
Very weird indeed.
In your "menu.lst" and "fstab" it says that Win98 is in "/dev/sda2", but in the last "fdisk -l" it says it is the Linux partition.
I'm not sure what to do. I would simply wipe out, erase, and reformat the Win98 partition, assuming you don't want it anymore.
Also, I would erase the line of "/dev/sda2" in "fstab".

I think it is tricky to use Windows to manage or edit partitions because it always messes up the Maser Boot Record. Use the Live CD instead for that.

I don't think you can damage your data. Keep trying and reading the forums. There are different solutions in different threads.

---

### Post by sarc on 2006-12-25
sda3 is the Win98 partition I deleted and then put back in hope of getting Ubuntu to boot
sda4 is my logical extended partition
sda 5, 7, 8 are my FAT32 shared drives between Ubuntu and WindowsXP
sad6 is my Linux swap drive


ARRRRRGHHH.. I an a nanosecond away from reinstaling from livecd... for the 38th time....

---

### Post by bulldog on 2006-12-25
Just modify your menu.lst and your fstab according the new situation.

Ubuntu is listed as (hd0,3) in menu list which points to sda4,it should be (hd0,1) pointing at sda2.

Fstab says /dev/sda2 is a vfat partition,it's not it's your ubuntu partition.

So you have to change menu.lst and fstab according the new situation,which you created by removing and recreating a partition.
```
itle		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,3)**<---should be (hd0,1)**
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda4 ro single**<---should be sda2 the same for all the other kernel entry's**
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows 95/98/Me
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```
```
# /etc/fstab: static file system information.
#
# &lt;file system&gt; &lt;mount point&gt;   &lt;type&gt;  &lt;options&gt;       &lt;dump&gt;  &lt;pass&gt;
proc            /proc           proc    defaults        0       0
# /dev/sda4**<--wrong should be sda2**
UUID=ee8e1850-efef-48c8-a818-a5d69e1ac217 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=05B4B59970DDA36F /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=54AA-9C0B  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1**<--delete this one and all of the non existing and modify the others according fdisk -l**
# /dev/sda5
UUID=1470-C70A  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=C41A-9E7B  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=349D-7DB0  /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=30e317ab-5535-4e15-a310-5316b9a2476c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0    
```

---

### Post by sarc on 2006-12-25
Thanks very much... fdsik -l does not give me UUID... what do I use for UUIDs in fstab?

---

### Post by Vox754 on 2006-12-25
I don't know if this helps, but next time set the swap partition at the beginning of the linux partitions.

For instance I have.
sda1    WinXP
sda2    fat32
sda3    (extended)

sda5   /boot
sda6   swap
sda7   /
sda8... rest of the tree

The UUIDs have something to do with permissions and groups. I don't know much.

---

### Post by sarc on 2006-12-26
YUUHUUUUUUU!

I can boot!

THANKS BULLDOG!

However my FAT32 share folders are mounted in the wrong place; and sda 3 and 5 are not mounted at all:

See Gparted attachments with the weird mounts (how do I change them thru GUI?  A bit afraid to try the console for this)

My current fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=05B4B59970DDA36F /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=ee8e1850-efef-48c8-a818-a5d69e1ac217 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=1470-C70A  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=C41A-9E7B  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=30e317ab-5535-4e15-a310-5316b9a2476c none            swap    sw              0       0
# /dev/sda7
UUID=349D-7DB0  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=349D-7DB0  /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Thx and Merry Xmas!

---

### Post by bulldog on 2006-12-26
Have a look here for the mounting problems.'

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

To find the UUID for any drive```
ls /dev/disk/by-uuid -lh
```

---

### Post by Ocxic on 2006-12-26
Make sure you change this line in your menu.lst:

```

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)    <--- Change this line  to "# groot=(hd0,1)"

```

to the change of your configuration or you'll have to re-edit the menu.lst file after ever kernel upgrade. don't uncomment the lines just edit.

---

### Post by sarc on 2006-12-28
IT WORKED!  I'm back in business!

Ocxic thanks for the tip.  Done.

p.s. CURSES on Windows who messed up my MBR.  I'm still stuck with it though.

---

