---
title: "I cant write on my USB disk(ext3) in ubuntu 8.04"
date: 2008-05-01
forum: General Help
---

### Post by rado3105 on 2008-05-01
I cant write on my USB disk with ext3 file system in ubuntu 8.04. The disk is mounted.

---

### Post by unutbu on 2008-05-01
We're going to need some more information.
Does the USB disk mount automatically or do you issue the mount command manually?

Please post the output of

```
mount
sudo fdisk -l
cat /etc/fstab
ls -ld <mount point>
```

---

### Post by rado3105 on 2008-05-05
mount, WD1TB is that disk
> /dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/r-c/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=r-c)
/dev/sdb1 on /media/WD1TB type ext3 (rw,nosuid,nodev,uhelper=hal)
> 
sudo fdisk -l sdb1 is that disk
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19657db4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2516    20209738+   7  HPFS/NTFS
/dev/sda2            2517       12161    77473462+   5  Extended
/dev/sda5            2517        9287    54388026    7  HPFS/NTFS
/dev/sda6            9288       11879    20820208+  83  Linux
/dev/sda7           11880       12161     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xdcde6b16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1     1938021   976762552+  83  Linux

cat /etc/fstab
> Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1     1938021   976762552+  83  Linux
r-c@r-c-laptop:~$ cat etc/fstba
cat: etc/fstba: No such file or directory
r-c@r-c-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=b625376f-0dd7-40b7-badd-4c6d6f1981a0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=05b2d529-133d-4f41-af7d-eea73bcc6361 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

r-c@r-c-laptop:~$ ls -ld /media/WD1TB
> drwxr-xr-x 28 root root 4096 2002-08-28 21:43 /media/WD1TB


Also can you tell me how to edit /etc/fstab to be NTFS partitions sda1 and sda 5 automounted after system start(in ubuntu 8.04 they are default unmounted and i must them mount manually

---

### Post by unutbu on 2008-05-05
So you can read,write,execute on WD1TB: First, mount /media/WD1TB. Then run:

```
sudo chown r-c.r-c /media/WD1TB
sudo chmod 770 /media/WD1TB

```
(assuming r-c is your username).

To mount /dev/sda1 and /dev/sda5:

First, create the mount points:

```
sudo mkdir /media/windows
sudo mkdir /media/data
```

You can change the names of the directories to whatever you want. Now run

```
ls -l /dev/disk/by-uuid/
```

You'll see something like
```
% ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-05-05 09:57 03a507ee-cdac-4bd9-b438-eccd616b66ed -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-05-05 09:57 33b7e11e-5bdb-4e98-b626-671b1c4d18eb -> ../../sda5
```

On each line, the long hyphenated hex string in the middle is the UUID (Universally Unique Identifier) for the partition. You'll need those in the next step:

```

sudo cp /etc/fstab /etc/fstab-orig
gksudo gedit /etc/fstab
```

Add these lines:
```
UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed /media/windows ntfs defaults 0 0
UUID=33b7e11e-5bdb-4e98-b626-671b1c4d18eb /media/data ntfs defaults 0 0
```

Of course, substitute the correct UUIDs for sda1 and sda5 in your fstab.

Reboot to make sure they auto mount and are readable/writable, etc. Once you are sure fstab is behaving the way you want, you may remove the backup copy of the original:

```
sudo rm /etc/fstab-orig
```

There is an excellent guide on how to fstab at [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by rado3105 on 2008-05-05
> sudo chown r-c.r-c /media/WD1TB
sudo chmod 770 /media/WD1TB

after using this commands I cant still write on WD1TB

---

### Post by unutbu on 2008-05-05
Please show output of
```
ls -ld /media/WD1TB
```

---

### Post by rado3105 on 2008-05-06
drwxrwx--- 28 r-c r-c 4096 2002-08-28 21:43 /media/WD1TB

---

### Post by niteshifter on 2008-05-06
Hi,

There's a typo in what unutbu posted. Try this:

```
sudo chown r-c:r-c /media/WD1TB
sudo chmod 770 /media/WD1TB 
```

To be clear: What comes after the chown is username, a colon (:), then groupname.

---

