---
title: "Harddrive performance issues"
date: 2006-08-04
forum: General Help
---

### Post by HAARP on 2006-08-04
Hi there,
I've got a problem with one of my drives.
```
hdparm -t /dev/hda
 Timing buffered disk reads:  132 MB in  3.02 seconds =  43.65 MB/sec
hdparm -t /dev/hda2
 Timing buffered disk reads:   108 MB in  3.02 seconds =  35.76 MB/sec
```
As you can see, performance is terrible on that particular partition. It's ReiserFS and mounted in **/**, but that shouldn't matter since hdparm performs raw tests. DMA is enabled.
Trying to copy files off it is even slower (file system overhead), but the major problem is that the system becomes unusable when I say, make a backup.
It takes several seconds to display a menu, half a minute to start something like gedit, etc. It blocks other operations out almost completely.
The other harddisk on the same controller has much better performance:
```
/dev/hdb2:
 Timing buffered disk reads:  190 MB in  3.01 seconds =  63.08 MB/sec
```
And my SATA RAID array is even faster:
```
/dev/md0:
 Timing buffered disk reads:  256 MB in  3.02 seconds =  84.88 MB/sec
```
So the IDE/PCI bus is not the issue. Any ideas? Thanks in advance.

My fstab:
```
# /etc/fstab: static file system information.
#
#<file system>	<mount point>	<type>		<options>				<dump>	<pass>

## System ##
proc		/proc		proc		defaults				0	0
/dev/hda2	/		reiserfs	notail					0	1

## Swap ##
/dev/hda3	none		swap		sw,pri=0				0	0
/dev/hdb1	none		swap		sw,pri=0				0	0
/dev/sda1	none		swap		sw,pri=0				0	0
/dev/sdb1	none		swap		sw,pri=0				0	0

## Data ##
/dev/md0	/data	reiserfs	notail					0	0
/dev/hdb2	/media/hdb2	ext2		defaults				0	0

## Windoze ##
/dev/hda1	/media/hda1	ntfs		defaults,ro,nls=utf8,umask=007,gid=46	0       0

## Removable ##
/dev/fd0	/media/floppy	ext2,vfat	user,noauto				0	0
/dev/hdd	/media/cdrom0	udf,iso9660	user,noauto				0	0
/dev/hdc	/media/cdrom1	udf,iso9660	user,noauto				0	0

```

---

