---
title: "File systems disappeared from desktop"
date: 2008-03-08
forum: General Help
---

### Post by Morot313 on 2008-03-08
So I am running 8.04 Hardy Heron (alpha).
There were some update, (gfvs I think).

I have 2 hard disks on my computer.
/dev/sda1 (ntfs) = Windows XP
/dev/sda5 (ntfs) = Media
/dev/sda6 (ntfs) = Media
/dev/sdb1 (ext3) = Ubuntu
/dev/sdb2 (ext3) = Backup

Before sda1, sda5, sda6, sdb2 were automatically mounted and visible on the desktop.

Now just sdb2 is automatically mounted and visible on the desktop.

sda1, sda5, sda6 are not on the desktop and not automatically mounted.
They're listed in "Places" menu though, and if I click on them, they get mounted.

I want them automounted and visible on the desktop, because Rhythmbox needs to access music on sda5.

---

### Post by taurus on 2008-03-08
Post

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Morot313 on 2008-03-08
```
$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ca0a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       60800   462776422+   f  W95 Ext'd (LBA)
/dev/sda5            3188       12748    76798701    7  HPFS/NTFS
/dev/sda6           12749       60800   385977658+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005dff8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3039    24410736   83  Linux
/dev/sdb2            3040       30401   219785265   83  Linux
```

```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=14b33efe-3a94-4c7f-9649-fd1b608f07d1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
/dev/sdb2       /media/sdb2     ext3    defaults,rw     0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              23G  4.6G   18G  22% /
varrun                1.7G   92K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   64K  1.7G   1% /dev
devshm                1.7G   52K  1.7G   1% /dev/shm
lrm                   1.7G   37M  1.6G   3% /lib/modules/2.6.24-11-386/volatile
/dev/sdb2             207G  534M  196G   1% /media/sdb2
/dev/sda6             369G   25G  344G   7% /media/Media
/dev/sda5              74G   19G   55G  26% /media/disk
```

---

### Post by taurus on 2008-03-08
> **Morot313 said:**
> 
```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              23G  4.6G   18G  22% /
varrun                1.7G   92K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   64K  1.7G   1% /dev
devshm                1.7G   52K  1.7G   1% /dev/shm
lrm                   1.7G   37M  1.6G   3% /lib/modules/2.6.24-11-386/volatile
/dev/sdb2             207G  534M  196G   1% /media/sdb2
[B][COLOR="Blue"]/dev/sda6             369G   25G  344G   7% /media/Media
/dev/sda5              74G   19G   55G  26% /media/disk[/COLOR][/B]

Well, both /dev/sda5 & /dev/sda6 are automounted to /media/disk & /media/Media.

Now, what happens if you run these commands to mount /dev/sda1?

[code]sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows -o umask=0222
df -h
```

---

### Post by Morot313 on 2008-03-08
No, sda5 ans sda6 are not auto-mounted.
I've used "Places" to open them, then they get mounted on-the-fly when I open them in "Places".

Initially on bootup, sda5 and sda6 are not visible on 'df -h'.

---

### Post by Morot313 on 2008-03-09
How exactly is this an improvement when before the updates, my partitions were automounted, and now after the update they're not?

---

