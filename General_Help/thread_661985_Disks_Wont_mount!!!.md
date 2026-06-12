---
title: "Disks Wont mount!!!"
date: 2008-01-08
forum: General Help
---

### Post by matt91 on 2008-01-08
I have an urgent problem with 2 of my hdd's not mounting. The server has been on 31 days and i did a restart only to find out 2 of my disks are not mounting, I tried to mount them manually:

```

root@server:~# mount -t ext3 /dev/sdb1 /data/storage
mount: /dev/sdb1 already mounted or /data/storage busy
root@server:~# mount -t ext3 /dev/sdc1 /data/storage_backup
mount: /dev/sdc1 already mounted or /data/storage_backup busy

```

This did not work so i commented out the lines in the fstab for these disks and restarted, tried mounting manually again with the same commands and i just got the same result.

My primary disk has all partitions mounted properly and webmin shows all disk with ok SMART status, i have even tried mounting the disks through the webmin interface. I have also tried mounting the disks to other newly created directories such as /mnt/test and it still does not work.

This is confusing as these are two seperate disks :confused:

Please can somebody help, i have all my files on these disks and i need to access something on them tonight. :( I have attatched a screenshot from webmin of the disks if this helps you understand my disks.

Matt

---

### Post by matt91 on 2008-01-08
Just if it helps, this is what fdisk shows, just the same as webmin, everything apart from sdb1 and sdc1 mounting :(

```
oot@server:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbea4bea4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15665   125829081   83  Linux
/dev/sda3           15666       19219    28547505   83  Linux
/dev/sda4           19220       19457     1911735   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux

```

---

### Post by p_quarles on 2008-01-08
Well, the output of mount is saying that the drive is either already mounted, or the mountpoint is busy. So, let's try to find out which it is:
```
df -h
```
should list drives and partitions that the kernel thinks are mounted.

```
lsof /data/storage
```
will attempt to list the process using the mountpoint.

---

### Post by matt91 on 2008-01-08
Dont get anything with those commands, this is very unusual, im sure it wont be a problem with the disks as they were working perfectly before the restart.

```
root@server:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              27G  2.8G   23G  11% /
varrun                506M  184K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   72K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/sda1             119G   19G   94G  17% /data/storage1

```

For both **lsof /data/storage** and **lsof /data/storage_backup** i dont get anything.

:confused:

---

### Post by p_quarles on 2008-01-08
Hmm. Is it possible that there's any data in the mountpoint?
```
ls -al /data/storage
```
If not, what happens when you run this?:
```
sudo umount /data/storage
```

---

### Post by matt91 on 2008-01-08
No data at the mount point, i recreated the dir so nothing in it.

```
root@server:/data/storage# ls -al /data/storage
total 8
drwxrwxrwx 2 root root 4096 2008-01-08 20:02 .
drwxrwxrwx 7 root root 4096 2008-01-08 20:02 ..

```

I have also tried the umount for both, just get:

```
root@server:/# umount /data/storage
umount: /data/storage: not mounted

```

---

### Post by p_quarles on 2008-01-08
Very strange indeed. I wonder if this has something to do with the disk IDs getting changed. Can you post the output of the following two commands?:
```
cat /etc/fstab
```
and 
```
ls -l /dev/disk/by-uuid
```

---

### Post by matt91 on 2008-01-08
my fstab:

```
root@server:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=dd9e2f64-e0a0-455c-a072-024b60ee4362 /               ext3    defaults,errors=remount-ro 0       1
UUID=45249df0-e078-4a3c-a923-826090f25718 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

UUID=62d5105e-63ed-4f90-9eac-e9768f92331a  /data/storage        ext3    defaults        0       0
UUID=a06be00b-f8b9-40d0-a3df-aecee84bd02d  /data/storage1  ext3  suid,dev,exec  0  0
UUID=35e416ec-6f67-4363-a02c-32cddaa5c794  /data/storage_backup ext3    defaults        0       0

```

```
root@server:/# ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-01-08 20:28 21a16b32-2442-4aca-86cf-5d0ee38bf616 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-01-08 20:28 35e416ec-6f67-4363-a02c-32cddaa5c794 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-01-08 20:28 62d5105e-63ed-4f90-9eac-e9768f92331a -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-01-08 20:28 a06be00b-f8b9-40d0-a3df-aecee84bd02d -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-01-08 20:28 dd9e2f64-e0a0-455c-a072-024b60ee4362 -> ../../sda3

```

UUID's havnt changed. I havn't changed anything within the 31 days the machine has been on that could have messed with disk mounting.

---

### Post by p_quarles on 2008-01-08
Eesh. This problem isn't going to give up easily, apparently.

I wonder what would happen if you made a new mount point for the drives, such as:
```
mkdir /mnt/testing123
```
Is it possible to mount sdb or sdc there?

---

### Post by matt91 on 2008-01-08
```
root@server:/data/storage# mkdir /mnt/testing123
root@server:/data/storage# mount -t ext3 /dev/sdc1 /mnt/testing123
mount: /dev/sdc1 already mounted or /mnt/testing123 busy

```

Not as simple as it seems.

I might try the livecd now to see if they mount with that.

Thank you for your help so far.

---

### Post by matt91 on 2008-01-08
LiveCD mounts them both automatically with all their data their.

I have also managed to mount my memory stick (FAT32) with no problems.

---

### Post by p_quarles on 2008-01-08
Well, this one has me thoroughly stumped. At least your data's all right, though. 

It seems like you might be able to use Gparted (the live CD version) to update the partition table. You can do this without actually formatting or resizing any of the partitions. Don't know if that will help, but it's certainly a less drastic measure than reinstalling (which, based on your resutls with the Ubuntu live disk, would be a viable solution).

---

### Post by matt91 on 2008-01-08
Will try that now. My setup has been modified a lot so i would prefer not to reinstall. I have an exam tomorrow so was just hoping i could have a quick fix (have to get revising now).

---

### Post by p_quarles on 2008-01-08
If you do find yourself needing to reinstall, I know a number of tricks for quickly restoring all of your modifications, so don't hesitate to ask.

---

### Post by matt91 on 2008-01-08
I actually do 2 backups a week  of  / onto /data/storage (which is backed up onto /data/storage_backup) so i will be able to copy stuff from that.

---

### Post by matt91 on 2008-01-08
Just ran gparted, did not know what you meant by update the partition table. I did the Partition > Check function. If that was correct then it didnt work :(

It is very frustrating since i know this would probably be sorted very easily (it usually is ;)).

Is their  a way to like "re-assign" the disks to ubuntu thinks they are fresh new disks (new UUID perhaps)?

Would probably be a few days until i get chance to reinstall Ubuntu.

---

### Post by matt91 on 2008-01-09
I have re-installed ubuntu and it works :)

Thank you for your help, hope it does not happen again. ;)

---

