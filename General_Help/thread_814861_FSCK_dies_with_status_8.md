---
title: "FSCK dies with status 8"
date: 2008-06-01
forum: General Help
---

### Post by gypaete09 on 2008-06-01
Hi,

I used to run Gutsy on /dev/sda2 (/dev/sda1 is still XP). 
I then upgraded Gutsy to Hardy via the net ( had made a live CD, though, that proved *very* useful later)

Hardy went freezing up more and more until it blocked totally, locking me out from anything but console commands, so I reinstalled Gutsy fresh on a different partition /dev/sdb2.

Now I mount the former gutsy boot partition as /home/data,
but more and more often, then always, the partition won't automount and I "fall" into the diag console.
There I can issue the "mount /dev/sda2" and "exit" commands and all goes on as it should.
/var/log/fsck fscheck shows that fsck dies with status 8

I checked output from blkid and content of fstab, as proposed by several posts here, and the UUID's shown for that the partition are identical.

what should I do? I don't want to fiddle with partition data before knowing what I do.

Here some data, maybe someone can find what's wrong.
(I also have a message regarding the superblock of my ext USB drive /dev/sdc1, but that's another ball game.

*********************************************************************
blkid:
/dev/sda1: UUID="4EC4BDDEC4BDC88B" LABEL="System" TYPE="ntfs" 
/dev/sda2: UUID="34b9fd77-4d59-4ba5-b310-0b8ca74c4f65" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="f7d2a2d3-7b2f-41fd-a278-73c371d996e3" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0A0F" TYPE="vfat" 
/dev/sdb2: UUID="fc12704b-3a1e-4058-87f0-39247046b5d4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sdc1: UUID="ed0f12bb-6da4-4d78-9a70-3a7f05c73ded" SEC_TYPE="ext2" TYPE="ext3" 

***********************************************************************
/etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=fc12704b-3a1e-4058-87f0-39247046b5d4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=4EC4BDDEC4BDC88B /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=34b9fd77-4d59-4ba5-b310-0b8ca74c4f65 /home/johan/data     ext3    defaults        0       2
# /dev/sdb1
UUID=07D6-0A0F  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb3       /media/sdb3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdc1
/dev/sdc1       /mnt/backup     ext3    defaults 0 2
UUID=f7d2a2d3-7b2f-41fd-a278-73c371d996e3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

************************************************************************
mount -l:
/dev/sdb2 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda2 on /home/johan/data type ext3 (rw) []
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096) [System]
/dev/sdb1 on /media/sdb1 type vfat (rw,utf8,umask=007,gid=46) [DellUtility]
/dev/sdb3 on /media/sdb3 type vfat (rw,utf8,umask=007,gid=46) [DellRestore]
/dev/sdc1 on /mnt/backup type ext3 (rw) []
securityfs on /sys/kernel/security type securityfs (rw)

**************************************************************************
/var/log/fsck/checkfs:
Log of fsck -C -R -A -a 
Sun Jun  1 10:02:45 2008

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb1: 83 files, 3696/24026 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb3: 1677 files, 582248/823724 clusters
fsck.ext3: No such file or directory while trying to open /dev/sdc1
/dev/sdc1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

/dev/sda2: clean, 201897/13615104 files, 9632922/27228166 blocks
fsck died with exit status 8

Sun Jun  1 10:02:46 2008

---

### Post by gypaete09 on 2008-07-15
How "nice" to see that no one could help... I still mount the failing partition by hand from the diag screen (mount /dev/sda2, then exit).
Sometimes it comes up by itself, but very rarely now.

It used to be the gutsy boot partition, then I updated via the net to Hardy, and finally had to go back to Gutsy while I wait for a solution for the freezes. (my one-man company depends on this PC).

Now I boot Linux from a different disk and use the former Hardy boot partition as home partition only. The superblock or whatever media descriptor
might have been changed by the hardy install and now is unusable for gutsy?

Anyway, if anyone has a solution, you're welcome.

G

---

