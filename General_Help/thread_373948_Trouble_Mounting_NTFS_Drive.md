---
title: "Trouble Mounting NTFS Drive"
date: 2007-03-01
forum: General Help
---

### Post by AndyCUI on 2007-03-01
fdisk results:

Disk /dev/sda: 74.3 GB, 74355769344 bytes
16 heads, 63 sectors/track, 144073 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      144073    72612760+  42  SFS

Disk /dev/sdb: 74.3 GB, 74354687488 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8669    69633711   83  Linux
/dev/sdb2            8670        9039     2972025    5  Extended
/dev/sdb5            8670        9039     2971993+  82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19452   156248158+   7  HPFS/NTFS


andy@andy-desktop:~$ sudo mount /dev/hdb1
mount: can't find /dev/hdb1 in /etc/fstab or /etc/mtab

I am still pretty new to Ubuntu and haven't had any luck yet.

Thanks

---

### Post by taurus on 2007-03-01
Edit /etc/fstab

```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Create a new mount point for it and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

