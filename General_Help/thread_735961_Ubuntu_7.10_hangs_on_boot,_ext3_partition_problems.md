---
title: "Ubuntu 7.10 hangs on boot, ext3 partition problems"
date: 2008-03-26
forum: General Help
---

### Post by menkhaf on 2008-03-26
**EDIT: Since I've tried my best (and failed), I've changed the title to solved. The solution was to reinstall Ubuntu -- not proud of it though.**

Hi!

I've been trying my best to make this work without turning to forums, but alas, I haven't really gotten anywhere yet.
I had a few days off last week because of easter, and decided to finally install Windows XP alongside my (almost new) Ubuntu 7.10 install. I'd rather stay with Linux only, but I missed a few games and I got nowhere with the current version of Wine.

I resized my ext3 (sda1) partition and made room for Windows on partition sda2. Installed Windows fine, reinstalled Grub and got Windows XP working through Grub and was happy for a short while. Right until I tried booting to Linux.

The beginning of the boot sequence is all good, but it stops when trying to mount the root file system. I've spent some time figuring out what is wrong, and I think that I got it.
```
root@ubuntu:/# fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
16 heads, 63 sectors/track, 193821 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x000dfd1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      135055    68067373+  83  Linux
/dev/sda2   *      135055      185848    25599577+   7  HPFS/NTFS
/dev/sda3          185848      193816     4016250    5  Extended
/dev/sda5          185848      193816     4016218+  82  Linux swap / Solaris
```

My partition table seems just fine. However, the following looks a bit wrong:
```
root@ubuntu:/# /lib/udev/vol_id /dev/sda1 
ID_FS_USAGE=filesystem
ID_FS_TYPE=vfat
ID_FS_VERSION=FAT12
ID_FS_UUID=
ID_FS_UUID_ENC=
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
```
I've tried mounting sda1 without specifying filesystem type after booting the Ubuntu 7.10 Live CD, and mount actually tries to mount the partition as VFAT:
```
root@ubuntu:/# mount /dev/sda1 /mnt/lol/
root@ubuntu:/# mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /mnt/lol type vfat (rw)
```
Needless to say, this doesn't really work out that great.

I've run fsck.ext3 a few times on the partition, but nothing really happens. I have a bit of backup-worthy data on the disk, so I'm a bit afraid to really mess around with it right now; I'll make a backup soon.

What I'm wondering about now is what I could do to rescue the partition without losing anything. As long as I specify the filesystem type the partition gets mounted without problems, but it's not really helping me with booting my Ubuntu install.

Any ideas would be greatly appreciated.

Thanks in advance!

---

### Post by justsomedude on 2008-03-26
Could you post your /etc/fstab file from your Linux partition?

---

### Post by menkhaf on 2008-03-26
> **justsomedude said:**
> Could you post your /etc/fstab file from your Linux partition?
Sure:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=765eaba9-74b9-41c0-a538-d2c1f3ec407d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b6a56eff-4c89-423f-8c11-434190a4f416 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```
As far as I can tell, I've hosed my superblock. I've read that ext2/3 creates a backup superblock, but I'm too afraid to run mkfs.ext3 -S -b 4096 before doing a small backup.

dumpe2fs gives me the following output:
```
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          765eaba9-74b9-41c0-a538-d2c1f3ec407d
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed directory hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              8519680
Block count:              17016843
Reserved block count:     680673
Free blocks:              3057808
Free inodes:              8149369
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1019
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Wed Feb 20 12:37:41 2008
Last mount time:          Wed Mar 26 10:39:05 2008
Last write time:          Wed Mar 26 11:06:02 2008
Mount count:              1
Maximum mount count:      22
Last checked:             Wed Mar 26 10:29:45 2008
Check interval:           15552000 (6 months)
Next check after:         Mon Sep 22 10:29:45 2008
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      c5510c9d-45f8-4f11-bf36-95e8888cfa52
Journal backup:           inode blocks
Journal size:             128M

```

---

### Post by justsomedude on 2008-03-26
Hm, your fstab and dump2fs output look allright, as far as I can tell.

Not sure what happened there, I'd propably reformat sda1 and install anew if I were you. Since you wrote above that your Ubuntu install is almost new, it won't be too much fuss as Ubuntu installs in 30 minutes.

You could use the [fs-driver]("http://www.fs-driver.org/") to access your partition from within windows (do not enable write support for the fs-driver, as it will mess up your ext3 journal) and make a backup this way.

Or, you try a manual repair with fsck /dev/sda1 before you reinstall.

Good luck...

---

### Post by menkhaf on 2008-03-26
I'm taking a backup to an external hard drive right now, and I think I'll try to recreate the superblock afterwards. I'll make sure to report back afterwards.

Thanks for the responses ;)

---

### Post by menkhaf on 2008-03-26
Well, I tried my best. Backed everything up, ran mkfs.ext2 to try to recreate the superblock:
```
ubuntu@ubuntu:~$ sudo mkfs.ext2 -v -F -S -b 4092 /dev/sda1 
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=2048 (log=1)
Fragment size=2048 (log=1)
8511488 inodes, 34033686 blocks
1701684 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=571473920
2078 block groups
16384 blocks per group, 16384 fragments per group
4096 inodes per group
Superblock backups stored on blocks: 
        16384, 49152, 81920, 114688, 147456, 409600, 442368, 802816, 1327104, 
        2048000, 3981312, 5619712, 10240000, 11943936

Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 37 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/ting/
ubuntu@ubuntu:~$ ls /mnt/ting/
"?<.$?<  "b?.$b?  "?u.$?u
ubuntu@ubuntu:~$ sudo umount /mnt/ting/
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/ting/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
As you can see, this didn't really help. I'm now doing a new Ubuntu install.

Once again, thanks for the replies.

/Menkhaf

---

