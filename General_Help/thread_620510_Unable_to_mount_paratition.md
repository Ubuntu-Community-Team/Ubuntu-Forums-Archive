---
title: "Unable to mount paratition"
date: 2007-11-22
forum: General Help
---

### Post by infinitelink on 2007-11-22
Okay, so I type:

sudo mount /windows

into the terminal and get

[sudo] password for USERNAME: PASSWORD

and I get:

fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda5 ()

and what's the deal, how does one fix it, and who knows vs. who would try to do a hack?

This is probably a simple one...but err. Thanks for any help you might be able to provide!

: )~!

B.

---

### Post by mpierce on 2007-11-22
Here's an example of how I mount my notebook using samba:

//dellbook/mpierce /media/xp    smbfs   ro,users,uid=mpierce,noauto,credentials=/home/mpierce/.smbpasswd00

I create a file in my home directory with only two entries:
   username=
   password=

I set file permissions on it to 600 owned by me. Only sudo can do the mount by I own all files and can rw.

Hope this helps.

---

### Post by taurus on 2007-11-22
Can you post

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by infinitelink on 2007-11-22
Here's what you were looking for: 
~$ sudo fdisk -l
[sudo] password for USERNAME:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb29bb29b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+   6  FAT16
/dev/sda2               7        6053    48572527+   f  W95 Ext'd (LBA)
/dev/sda3            6054       12160    49054477+   c  W95 FAT32 (LBA)
/dev/sda5               7        3193    25599546    7  HPFS/NTFS
/dev/sda6            4852        5106     2048256   82  Linux swap / Solaris
/dev/sda7            5107        5107           0+  83  Linux
/dev/sda8            3194        3194           0+  83  Linux
/dev/sda9            5107        6053     7606746    b  W95 FAT32
/dev/sda10           3194        4851    13317853+  83  Linux

Partition table entries are not in disk order
jb@AGFTL:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
UUID=11dbf099-f7d1-4555-b0d3-6bbc19f3894a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D4-0B04  /dos            vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=463A-14E5  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=4453-BDBA  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=7A94A8C394A8836D /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=1eb1cfe1-6e23-4a20-a216-57c7e6e7fa04 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
jb@AGFTL:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda10             13G  8.0G  4.0G  67% /
varrun               1014M  100K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
udev                 1014M   88K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              47M  7.4M   40M  16% /dos
/dev/sda9             7.3G  963M  6.3G  13% /media/sda1
/dev/sda3              47G   36G   12G  76% /media/sda2
/dev/sda5              25G   19G  6.5G  74% /windows
/dev/scd0             4.0M  4.0M     0 100% /media/cdrom0


: )

---

### Post by taurus on 2007-11-22
Looks like all your ntfs/vfat partitions are mounted and the only two partitions are not being mounted right now are the Linux ones:  /dev/sda7 & /dev/sda8.

---

### Post by infinitelink on 2007-11-22
Yet I cannot see those partitions...?? I can't type-in the path into the "address bar", and if I do 

sudo umount /dev/sda5    or

sudo umount /windows

and then mount them...no probs in terminal but it doesn't show up. : (

I'm also unable to mount either sda7 or sda8.

---

### Post by taurus on 2007-11-22
```
ls -la /windows
```

And if you want to mount /dev/sda7 & /dev/sda8, you need to edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/sda7   /media/sda7   ext3   defaults   0   1
/dev/sda8   /media/sda8   ext3   defaults   0   1
```
Save it.  Then, create those two new mount points and mount them.

```
sudo mkdir /media/sda7 /media/sda8
sudo mount -a
df -h
```

p.s.  If you want /dev/sda5 to appear on your desktop, you need to mount it to /media.  So, change this one, /windows, in /etc/fstab to /media/windows.  Then, run

```
sudo mkdir /media/windows
sudo umount /windows
sudo mount -a
df -h
```

---

