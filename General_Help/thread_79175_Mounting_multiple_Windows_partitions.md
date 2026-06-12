---
title: "Mounting multiple Windows partitions"
date: 2005-10-19
forum: General Help
---

### Post by TheEHMan on 2005-10-19
On my system hdb is a drive w/ multiple windows partitions.  I tried mounting the partitions w/ info found in the starter guide, but instead I have several windows partitions showing up on my desktop that are all the same drive.  I added this to fstab and saved:

/dev/hdb1       /media/windows  ntfs  iocharset=utf8,umask=000   0       0
/dev/hdb2       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb5       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb6       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb7       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb8       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb9       /media/windows  vfat    iocharset=utf8,umask=000   0       0

My partition table showed this:

Disk /dev/hdb: 20.4 GB, 20491075584 bytes
16 heads, 63 sectors/track, 39704 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        6615     3333456    7  HPFS/NTFS
/dev/hdb2            6615       39685    16667437+   f  W95 Ext'd (LBA)
/dev/hdb5            6615       13229     3333456    b  W95 FAT32
/dev/hdb6           13229       19843     3333456    b  W95 FAT32
/dev/hdb7           19843       26457     3333456    b  W95 FAT32
/dev/hdb8           26457       33071     3333456    b  W95 FAT32
/dev/hdb9           33071       39685     3333456    b  W95 FAT32


Where did I screw up?  This disk is my old Windoze install but it has a lot of music files and data I need to access.

---

### Post by chaumurky on 2005-10-19
You need a different mount point for each drive. E.g.

 /dev/hdb1       /media/windows**1** ntfs  iocharset=utf8,umask=000   0       0
 /dev/hdb2       /media/windows**2** vfat    iocharset=utf8,umask=000   0       0
 /dev/hdb5       /media/windows**3** vfat    iocharset=utf8,umask=000   0       0
 /dev/hdb6       /media/windows**4** vfat    iocharset=utf8,umask=000   0       0
 /dev/hdb7       /media/windows**5** vfat    iocharset=utf8,umask=000   0       0
 /dev/hdb8       /media/windows**6** vfat    iocharset=utf8,umask=000   0       0
 /dev/hdb9       /media/windows**7** vfat    iocharset=utf8,umask=000   0       0

---

### Post by TheEHMan on 2005-10-19
Excellent!:smile:   I did that but I got this reply when I tried to remount fstab:

mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The first partition showed up but that's all, I guess because of the error.:confused:

---

### Post by chaumurky on 2005-10-19
why don't you install gparted** (sudo apt-get install gparted) **and have a look at these partitions 'gui' style. You can perhaps see if they're really fat32 or not. That looks like what the error is. Also the first line you have (the ntfs one) should be:
[B]/dev/hdb1       /media/windows  ntfs    [COLOR=Red]nls=utf8,umask=0222[/COLOR] 0       0

[/B]Note the umask - you can't write to ntfs in Ubuntu.

EDIT: noticed something else...

---

### Post by TheEHMan on 2005-10-19
[QUOTE=chaumurky]
[B]/dev/hdb1       /media/windows  ntfs    [COLOR=Red]nls=utf8,umask=0222[/COLOR] 0       0

[/B]Note the umask - you can't write to ntfs in Ubuntu.
[/QUOTE]

Thanks, chaumurky.  I edited the fstab on the NTFS partition.  I can now see all the partitions when I go into /media/windows (I left out partition2 since it wasn't important).  Now, however, I have several windows drives on my desktop that still all point to the same partition.  I remounted fstab to no avail and tried logging out and back in.  In File Browser these are listed on the left side as WINDOWS, WINDOWS (2), (3), (4), (5).
At the risk of being a pain, how can I get rid of these and the ones on my desktop and have the right ones show instead.

Thanks for all the help so far!

---

### Post by chaumurky on 2005-10-19
I'm not sure I understand. You're saying you have several mount points to the same drive? List what you have on the desktop and also post your /etc/fstab entries.

---

### Post by TheEHMan on 2005-10-19
FSTAB:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/windows1  ntfs  nls=utf8,umask=0222 0       0
/dev/hdb5       /media/windows2  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb6       /media/windows3  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb7       /media/windows4  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb8       /media/windows5  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb9       /media/windows6  vfat    iocharset=utf8,umask=000   0       0


Desktop (drive icons):
windows
windows (2)
windows (3)
windows (4)
windows (5)
windows1

Windows1 is OK.  The others are all pointing towards the same drive.  This is from an earlier attempt to mount them (see initial post).

---

### Post by chaumurky on 2005-10-19
I'm assuming you have rebooted and they haven't gone away. Try **sudo umount /media/w* ** Also, have you created the other paths for mounting i.e.

[B]sudo mkdir /media/windows2
[/B][B]sudo mkdir /media/windows3
[/B]etc.

When that's done go **sudo mount -a** again.

---

### Post by TheEHMan on 2005-10-20
I rebooted and that did the trick.  Thanks for all your help!:D

---

