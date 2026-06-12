---
title: "Moving files and permissions"
date: 2008-02-27
forum: General Help
---

### Post by Teleost on 2008-02-27
I'm using Kubuntu 7.10.

When I plug in my camera, I prefer to move the files by hand into the directories I want them in.

When I do though Dolphin spits up a dialog box saying "Could not change permissions for /media/sda5/blahblahblah".

This also happens when moving a number of other files between partitions.

The permissions on the moved files are fine but I constantly get this annoying box popping up, which when you're moving 100 or more files makes it a pretty painful process.

Is there a way to turn this off?

---

### Post by taurus on 2008-02-27
What filesystem is /dev/sda5 (mounted to /media/sda5)?

Post the outputs of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by Teleost on 2008-02-27
sda5 is NTFS

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4bdc4bd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            4498        4865     2955960   82  Linux swap / Solaris
/dev/hda3            2551        4497    15639277+  83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20a0209f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5099    40957686   83  Linux
/dev/sda2            5100       38912   271602922+   f  W95 Ext'd (LBA)
/dev/sda5            5100       17847   102398278+   7  HPFS/NTFS
/dev/sda6           17848       38912   169204581    7  HPFS/NTFS
teleost@teleost-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=4276b210-e8b2-43de-8ada-5be311c66be0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=6b129b84-cc1f-4db0-94cc-c56baf44dd71 /home           ext3    defaults        0       2
# /dev/hda1
UUID=E82458292457F8D0 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=DC940AFF940ADBC0 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=C44CD0CE4CD0BBFC /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda2
UUID=87654958-0d9a-4194-b6a9-8eeb15445fb7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
teleost@teleost-desktop:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /home type ext3 (rw)
/dev/hda1 on /media/hda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda6 on /media/sda6 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

### Post by taurus on 2008-02-27
I would mount those three ntfs filesystem partitions with ntfs-3g so you can write to them.

Edit /etc/fstab and replace these three lines

```

# /dev/hda1
UUID=E82458292457F8D0 /media/hda1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda5
UUID=DC940AFF940ADBC0 /media/sda5 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda6
UUID=C44CD0CE4CD0BBFC /media/sda6 ntfs defaults,umask=007,gid=46 0 1

```

with these new ones.

```

# /dev/hda1
UUID=E82458292457F8D0 /media/hda1 ntfs-3g defaults 0 0
# /dev/sda5
UUID=DC940AFF940ADBC0 /media/sda5 ntfs-3g defaults 0 0
# /dev/sda6
UUID=C44CD0CE4CD0BBFC /media/sda6 ntfs-3g defaults 0 0

```
Save it.  Then, install the ntfs-3g driver and reboot.

```
sudo apt-get update
sudo apt-get install ntfs-3g
```

---

### Post by sisco311 on 2008-02-27
> **taurus said:**
> I would mount those three ntfs filesystem partitions with ntfs-3g so you can write to them.

Edit /etc/fstab and replace these three lines

```

# /dev/hda1
UUID=E82458292457F8D0 /media/hda1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda5
UUID=DC940AFF940ADBC0 /media/sda5 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda6
UUID=C44CD0CE4CD0BBFC /media/sda6 ntfs defaults,umask=007,gid=46 0 1

```with these new ones.

```

# /dev/hda1
UUID=E82458292457F8D0 /media/hda1 ntfs-3g defaults 0 0
# /dev/sda5
UUID=DC940AFF940ADBC0 /media/sda5 ntfs-3g defaults 0 0
# /dev/sda6
UUID=C44CD0CE4CD0BBFC /media/sda6 ntfs-3g defaults 0 0

```Save it.  Then, install the ntfs-3g driver and reboot.

```
sudo apt-get update
sudo apt-get install ntfs-3g
```

I think the fstab is ok. Gusty Gibbon comes with built in ntfs support.

> [Teleost]("http://ubuntuforums.org/member.php?u=500133")Can you please post the output from:
```
ls -al /media
```and
```
id
```

---

### Post by bodhi.zazen on 2008-02-27
There may be two problems.

First ntfs does not support permissions, permissions are set at the time of mount via umask

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

Second, the ntfs drive = ro 

You need the ntfs-3g driver for write access.

---

