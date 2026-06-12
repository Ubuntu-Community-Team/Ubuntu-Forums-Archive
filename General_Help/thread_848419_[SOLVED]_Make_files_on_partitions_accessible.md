---
title: "[SOLVED] Make files on partitions accessible"
date: 2008-07-03
forum: General Help
---

### Post by njd4k on 2008-07-03
Hi,

I'm sure this is an easy problem to solve, but I don't even know what the name is for what I'm trying to do.

I keep all my files on a separate FAT32 partition shared with Win XP. When I start up, the shared partition is mounted, but the files are not accessible to my software. E.g. if I open Rhythmbox it dumps all my music out of the library into Import Errors, my desktop photo does not load, and so on. These problems are solved as soon as I open a file browser window on the partition, but it's annoying to have to do every time.

Is there a way to change this to make the partition as automatically available as my Ubuntu boot partition? I tried installing the Storage Device Manager, but that doesn't seem to have the option I'm looking for.

---

### Post by drs305 on 2008-07-03
Permissions on vfat files are set on mounting. You can edit your fstab and modify the mount permissions to allow the files on this partition to be available to the user on boot.

Backup fstab and edit:
```
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```

If you make your fat32 partition entry something like below it will allow it to automount with you as the owner (make sure the mountpoint exists):

```
/dev/sda8 /media/*mountpoint* vfat utf8,uid=1000,gid=100,umask=027 0 0 

```

If you don't know the vfat address or want to use UUID's and don't know them:
```

sudo fdisk -l
sudo blkid

```

---

### Post by njd4k on 2008-07-04
That worked perfectly. Thanks very much.

---

