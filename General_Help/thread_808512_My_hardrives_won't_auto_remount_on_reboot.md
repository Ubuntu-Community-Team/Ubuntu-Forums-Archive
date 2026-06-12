---
title: "My hardrives won't auto remount on reboot"
date: 2008-05-26
forum: General Help
---

### Post by eppi on 2008-05-26
I just installed Ubuntu 8.04. 

The only problem is that when I reboot my system my hardrives won't show up on my desktop. I have to press go in to the menu and press the removable media choice. All my hardrives are listed there but they won't show up on my desktop before I have pressed them.

---

### Post by cdtech on 2008-05-26
They should be listed in you /etc/fstab file to automount.

What do you get with:
sudo fdisk -l

---

### Post by strabes on 2008-05-26
That probably means that they're not mounted. Please paste the output of the following commands in a terminal (Applications > Accessories > Terminal).

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by eppi on 2008-05-27
THIS IS MY OUTPUT:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
48 heads, 46 sectors/track, 442379 cylinders
Units = cylinders of 2208 * 512 = 1130496 bytes
Disk identifier: 0xcc325102

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      442379   488384512    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf624f624

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1216     9767488+   5  Extended
/dev/sdb2            1217        2189     7815622+  82  Linux swap / Solaris
/dev/sdb3            2190       38913   294985530    7  HPFS/NTFS
/dev/sdb5               1        1216     9767457   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97a0ccab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        6375    51200000    7  HPFS/NTFS
/dev/sdc2            6375       38914   261368832    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa52459d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30400   244187968+   c  W95 FAT32 (LBA)

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       19457   156288321    7  HPFS/NTFS

---

### Post by eppi on 2008-05-28
bump

---

### Post by Zorael on 2008-05-28
And the contents of [FONT="Courier New"]/etc/fstab[/FONT]?

---

### Post by eppi on 2008-05-28
Sorry forgot it....

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=c3a209bb-de6d-421d-8c57-23de2495f7a0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=4328a383-3654-4dac-aa04-7b4509ff4372 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Zorael on 2008-05-28
Please use code tags when posting terminal output and other tabbed text.

To parse:
```
/dev/sda1	*	1	442379	488384512	7	HPFS/NTFS

/dev/sdb5		1	1216	9767457		83	Linux
/dev/sdb2		1217	2189	7815622+	82	Linux swap / Solaris
/dev/sdb3		2190	38913	294985530	7	HPFS/NTFS

/dev/sdc1		1	6375	51200000	7	HPFS/NTFS
/dev/sdc2		6375	38914	261368832	7	HPFS/NTFS

/dev/sdd1	*	1	30400	244187968+	c	W95 FAT32 (LBA)

/dev/sde1	*	1	19457	156288321	7	HPFS/NTFS
```
Out of these you only have sdb5 and sdb2 defined in fstab. And those partition tables are a mess, heh.

I'm hardly an expert on fstab configuration, but I'd try making a backup of it, and then replacing its contents with the following. You may want to ensure that you have a backup live CD at hand, but it shouldn't prove necessary.
```
########## root
/dev/sdb5	/		ext3		rw,relatime,errors=remount-ro 1 0

########## sda1
/dev/sda1	/media/sda1	ntfs-3g		defaults 2 0

########## sdb minus root
/dev/sdb2	none		swap		sw 0 0
/dev/sdb3	/media/sdb3	ntfs-3g		defaults 2 0

########## sdc
/dev/sdc1	/media/sdc1	ntfs-3g		defaults 2 0
/dev/sdc2	/media/sdc2	ntfs-3g		defaults 2 0

########## sdd
/dev/sdd1	/media/sdd1	vfat		defaults 2 0

########## sde
/dev/sde1	/media/sde1	ntfs-3g		defaults 2 0

########## removable
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8 0 0
/dev/fd0	/media/floppy0	auto		rw,user,noauto,exec,utf8 0 0
```
Pay special attention to the /media/sd* directories. These must exist, so create them if necessary. And obviously, if you want to rename them to something else, feel free.

To see if it works, enter this in a terminal.
```
$ sudo mount -a
```
There's plenty of tweaking you can do at this point, to set up proper permissions to your mounts. Not to mention charset for your files. See [http://www.swerdna.net.au/linhowtontfs.html](http://www.swerdna.net.au/linhowtontfs.html) for a guide to ntfs-3g options, and you might want to give the man pages for ntfs-3g and vfat a look.

If mount -a doesn't work and just spews error messages, post them here. You can always revert to your old fstab, provided you made a backup of it.

---

### Post by eppi on 2008-05-28
That didn't work. The are still listed under Places --> Removable Media

When I tried ```
sudo mount -a
```
i got this:
```

fuse: failed to access mountpoint /media/sda1: No such file or directory
fuse: failed to access mountpoint /media/sdb3: No such file or directory
fuse: failed to access mountpoint /media/sdc1: No such file or directory
fuse: failed to access mountpoint /media/sdc2: No such file or directory
mount: mount point /media/sdd1 does not exist
fuse: failed to access mountpoint /media/sde1: No such file or directory

```

---

### Post by Der_Idiot on 2008-05-28
Thank you, I was looking for this very information! :)

---

### Post by Der_Idiot on 2008-05-28
Did you even read his post??

You need to MAKE ALL THE DIRS that gave you that error.

---

### Post by Zorael on 2008-05-28
> **eppi said:**
> That didn't work. The are still listed under Places --> Removable Media

When I tried ```
sudo mount -a
```
i got this:
```

fuse: failed to access mountpoint /media/sda1: No such file or directory
fuse: failed to access mountpoint /media/sdb3: No such file or directory
fuse: failed to access mountpoint /media/sdc1: No such file or directory
fuse: failed to access mountpoint /media/sdc2: No such file or directory
mount: mount point /media/sdd1 does not exist
fuse: failed to access mountpoint /media/sde1: No such file or directory

```
Please see text highlighted in bold.
> **Zorael said:**
> Pay special attention to the /media/sd* directories. **These must exist, so create them if necessary.** And obviously, if you want to rename them to something else, feel free.

---

### Post by eppi on 2008-06-02
i tried to make them but I got this. You probably already understand I am now Linux experts... So i'm sorry if I dont understand what you mean sometimes.

```
[mntent]: line 5 in /etc/fstab is bad
[mntent]: line 9 in /etc/fstab is bad
[mntent]: line 19 in /etc/fstab is bad
ntfs-3g: Failed to access volume '/dev/Lagring': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
ntfs-3g: Failed to access volume '/dev/Instalering': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
mount: special device /dev/EKSTERN does not exist

```

this is my fstab:

```
########## root
/dev/sdb5	/						ext3		rw,relatime,errors=remount-ro 1 0

########## sda1
/dev/302,1\ GB\ Media		/media/302,1\ GB\ Media		ntfs-3g		defaults 2 0

########## sdb minus root
/dev/sdb2			none				swap		sw 0 0
/dev/52,4\ GB\ Media		/media/52,4\ GB\ Media		ntfs-3g		defaults 2 0

########## sdc
/dev/Lagring			/media/Lagring			ntfs-3g		defaults 2 0
/dev/Instalering		/media/Instalering		ntfs-3g		defaults 2 0

########## sdd
/dev/EKSTERN			/media/EKSTERN			vfat		defaults 2 0

########## sde
/dev/WD\ Disk			/media/WD\ Disk Media		ntfs-3g		defaults 2 0

########## removable
/dev/scd0			/media/cdrom0			udf,iso9660	user,noauto,exec,utf8 0 0
/dev/fd0			/media/floppy0			auto		rw,user,noauto,exec,utf8 0 0
```

---

### Post by Zorael on 2008-06-03
Okay. You want it to look like this.

The first column with /dev/* should not be modified, only the second one. Spaces are expressed with "**\040**", so "A Directory With Stuff" becomes "A**\040**Directory**\040**With**\040**Stuff". Messy, I know.

```
########## root
/dev/sdb5			/				ext3		rw,relatime,errors=remount-ro 1 0

########## sda1
/dev/sda1			/media/302,1**\040**GB**\040**Media	ntfs-3g		defaults 2 0

########## sdb minus root
/dev/sdb2			none				swap		sw 0 0
/dev/sdb3			/media/52,4**\040**GB**\040**Media	ntfs-3g		defaults 2 0

########## sdc
/dev/sdc1			/media/Lagring			ntfs-3g		defaults 2 0
/dev/sdc2			/media/Instalering		ntfs-3g		defaults 2 0

########## sdd
/dev/sdd1			/media/EKSTERN			vfat		defaults 2 0

########## sde
/dev/sde1			/media/WD**\040**Disk**\040**Media	ntfs-3g		defaults 2 0

########## removable
/dev/scd0			/media/cdrom0			udf,iso9660	user,noauto,exec,utf8 0 0
/dev/fd0			/media/floppy0			auto		rw,user,noauto,exec,utf8 0 0
```

The above fstab would require the following directories to exist:
[list][*]/media/"302,1 GB Media"
[*]/media/"52,4 GB Media"
[*]/media/Lagring
[*]/media/Instalering
[*]/media/EXTERN
[*]/media/"WD Disk Media"
[*]/media/cdrom0
[*]/media/floppy0[/list]

---

### Post by TalioGladius on 2008-06-05
Awesome, just the info I was looking for.

---

