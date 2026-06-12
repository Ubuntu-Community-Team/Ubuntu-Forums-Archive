---
title: "Issues with partitions and file systems"
date: 2008-02-09
forum: General Help
---

### Post by totalnub on 2008-02-09
well, I just got an eee pc with xandros on it, and decided that I did not like their unionfs setup where /dev/sda1 would be ro and /dev/sda2 would mount on top. I've followed a how-to on booting into the "protected" partition (/dev/sda1) and can run and install anything i want. 

the problem is, the hdd is a 2GB SSD. i want to have as much space as possible in one large partition. 

right now the partition table looks like this:

/dev/sda1    1.4GB (1.2 used)
/dev/sda2    roughly 400MB

i've wiped /dev/sda2 clean and can mount it just fine. the problem happens when i go to resize the 1st partition. the error i get when running e2fsck -v /dev/sda1 is:

```
The filesystem size (according to the superblock) is 1502048 blocks
The physical size of the device is 1502046 blocks
Either the superblock or the partition table is likely to be corrupt!
```

I can't figure out what to do >.<

---

### Post by mrsteveman1 on 2008-02-09
run the following commands and post the results 

```
sudo mount
```

To see the mounted FS

```
sudo fdisk -l
```

To see the partitions

Also run ```
sudo fsck /dev/sda1
```

Instead of e2fsck, to make sure fsck uses the right fs when checking the disk. Note however that fsck shouldn't be running on a mounted filesystem anyway, but you can do it in single user mode.

---

### Post by totalnub on 2008-02-10
[COLOR="DarkRed"]Edit: I went ahead and wrote a new partition table....using fdisk last night before i posted this. All was good until i went to reboot into the first partition, and nothing happened. This laptop has no cd drive, so everything is usb booted. I ran the ASUS backup utility, and it seemingly restored things to a working order, however, the partition table is a little goofy now, and i get a file not found error when trying to boot into the first (protected) partition.

at this moment, unionfs is still intact. Let me know if you need any more information.[/COLOR]

kk

sudo mount gives me

```

sudo mount
rootfs on / type rootfs (rw)
/dev/sda1 on / type ext2 (ro)
unionfs on / type unionfs (rw,dirs=/=rw:/=ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw)
tmpfs on /dev/shm type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
```

sudo fdisk -l:
```

sudo fdisk -l

Disk /dev/sda: 2000 MB, 2000388096 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         187     1502046   83  Linux
/dev/sda2             188         241      433755   83  Linux
/dev/sda3             242         242        8032+   c  W95 FAT32 (LBA)
/dev/sda4             243         243        8032+  ef  EFI (FAT-12/16/32)

```

and sudo fsck /dev/sda1 is:

```

fsck /dev/sda1
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
Couldn't find ext2 superblock, trying backup blocks...
/sbin/e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

---

### Post by totalnub on 2008-02-10
bump

---

### Post by mrsteveman1 on 2008-02-12
So for right now what you are trying to do is boot into sda1 as if it were the only partition so that you can install and remove things, right?

And when you try to do this, where does the file not found error appear? at which point in the boot process?

---

