---
title: "Mounting HDD with superblock problems"
date: 2014-07-12
forum: General Help
---

### Post by dstu69 on 2014-07-12
Hello,

I connected a HDD that was running on a server that stopped functioning to an Ubuntu server, but I don't succeed to mount it.

These are the results of fdisk and fsck commands:
> root@server:~# fdisk -l

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 15200 cylinders, total 244190646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d2969

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064  3519112712   83  Linux

> root@server:~# fsck /dev/sdb1
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Can anyone help me? I have extremely important information on that disk.

Thanks in advance,

David

---

### Post by dragonfly41 on 2014-07-12
search for articles on repairing bad superblock .. here is one ..

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

and another ...

[https://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks](https://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks)

---

### Post by dstu69 on 2014-07-12
Hi dragonfly,

I tried to follow the instructions in the 1st link (using the backup super blocks), but ran into 2 types of errors on practically all the locations of the backups:
> root@server:~# mke2fs -n /dev/sdb1
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
61054976 inodes, 244190583 blocks
12209529 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
7453 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848


> 
root@server:~# e2fsck -b 32768 /dev/sdb1
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: [COLOR="#FF0000"]**Bad magic number in super-block while trying to open /dev/sdb1**[/COLOR]

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

root@server:~# e2fsck -b 98304 /dev/sdb1
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: [COLOR="#FF0000"]**Bad magic number in super-block while trying to open /dev/sdb1**[/COLOR]

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

root@server:~# e2fsck -b 214990848 /dev/sdb1
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: [COLOR="#0000FF"]**Invalid argument while trying to open /dev/sdb1**[/COLOR]

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>



Any idea?

Thanks,

David

---

### Post by dragonfly41 on 2014-07-12
Have you really tried on all 18 possibilities ...

> 32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848

---

### Post by dstu69 on 2014-07-12
> **dragonfly41 said:**
> Have you really tried on all 18 possibilities ...

I did. The 1st half of the values return the **bad magic **error and the rest return the **invalid **error :-(

---

### Post by dragonfly41 on 2014-07-12
> I have extremely important information on that disk.

It would be prudent to now clone the disk using **clonezilla** so you can work on recovery of data from the cloned image.

I would then use **testdisk** to try to recover data.

[later edit ...]

More notes on testdisk search for superblock

Here is one thread giving example of user needing to run testdisk which can look for superblocks (and recover data)

[https://bbs.archlinux.org/viewtopic.php?pid=1055262](https://bbs.archlinux.org/viewtopic.php?pid=1055262)


sudo testdisk

Create a new log file
Proceed
Intel
Advanced
select drive /dev/sdb1
select [Type] > [Superblock]

---

### Post by dragonfly41 on 2014-07-13
> I connected a HDD that was running on a server that stopped functioning to an Ubuntu server, but I don't succeed to mount it.

Referring back to your original symptoms .. have you run smartctl on external drive as explained in this thread ...

[http://forums.opensuse.org/showthread.php/455319-Repair-of-superblock-failing-What-next](http://forums.opensuse.org/showthread.php/455319-Repair-of-superblock-failing-What-next)

---

### Post by dstu69 on 2014-07-15
That's what I get with smartctl:

> root@server:~# smartctl /dev/sdb1
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-30-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

SCSI device successfully opened

Use 'smartctl -a' (or '-x') to print SMART (and more) information

root@server:~# smartctl -a /dev/sdb1
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-30-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Vendor:               WDC WD10
Product:              EARS-00Y5B1
User Capacity:        1,000,204,886,016 bytes [1.00 TB]
Logical block size:   4096 bytes
Device type:          disk
Local Time is:        Tue Jul 15 08:37:12 2014 IDT
SMART support is:     Unavailable - device lacks SMART capability.

=== START OF READ SMART DATA SECTION ===

Error Counter logging not supported

Device does not support Self Test logging


---

### Post by dragonfly41 on 2014-07-15
You could try the smartctl -T permissive option as detailed here ...

[https://superuser.com/questions/482404/check-ssd-health-without-using-smart](https://superuser.com/questions/482404/check-ssd-health-without-using-smart)

smartctl -T permissive -s on /dev/sdb1


If that does not work see other diagnostic tools referred to in above thread (e.g. ultimatebootcd can be used as live CD to test your external disk /dev/sdb1) ... download and burn to CD. Useful to keep in your toolbox for future recoveries.

[http://askubuntu.com/questions/194509/diagnoses-live-os](http://askubuntu.com/questions/194509/diagnoses-live-os)

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

