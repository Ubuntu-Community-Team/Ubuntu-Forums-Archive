---
title: "help with mount points"
date: 2015-11-05
forum: General Help
---

### Post by Deucalion29710 on 2015-11-05
I'm trying to get my system back the way that it was and I'm not good  with fstab.  I need to create a mount point for two drives naming them  Drive1 and Drive2.  How do I create the mount points and what do I add  to fstab?  Here is the output of the two drives:
 Disk /dev/sdb: 250.1 GB, 250059350016 bytes
 255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x00046042
    Device Boot      Start         End      Blocks   Id  System
 /dev/sdb1   *        2048   488394751   244196352   83  Linux
 Disk /dev/sdc: 500.1 GB, 500079525888 bytes
 255 heads, 63 sectors/track, 60797 cylinders, total 976717824 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0xec9e66fa
 It would be for these:
 /dev/sdb1: UUID="b5c005c9-ace8-4aaf-a5cd-a3614353a0b1" TYPE="ext4" 
 /dev/sdc1: LABEL="My Passport" TYPE="ntfs"

This is the output of my fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=48457920-395c-4ec5-815e-65aa02a23bba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e38363c5-8c4a-4176-bf6c-acc56781c35c none            swap    sw              0       0


Exactly how do I create these mount points and how should I edit my fstab appropriately so that both drives mount every time I boot my PC?  And of course I'm using Ubuntu 14.04.3 with GNOME

---

### Post by tturrisi on 2015-11-05
Here's how I do it. I mount my Win7 ntfs partition and a Files ntfs partition read-write.  As root I made 2 dirs: /media/Win7 and /media/Files.
fstab:
/dev/sda1    /media/Win7    ntfs-3g    defaults,uid=1000,gid=1000,umask=0000,fmask=0111    0    0
/dev/sda2    /media/Files    ntfs-3g    defaults,uid=1000,gid=1000,umask=0000,fmask=0111    0    0

Make 2 dirs in /media Drive1 and Drive2
```
/dev/sdb1	/media/Drive1	ext4	rw,user,exec,umask=000	0	0
/dev/sdc1	/media/Drive2	ntfs-3g	defaults,uid=1000,gid=1000,umask=0000,fmask=0111	0	0
```

---

### Post by yancek on 2015-11-05
A mount point is simply a directory so you would just use the terminal and create them.  The standard place to mount is the /mnt directory so:

```
sudo mkdir /mnt/Drive1
```

Repeat for Drive2.  For the Linux partition on sdb1 you could use:

> /dev/sdb1 /mnt/Drive1               ext4    errors=remount-ro 0       1

That is, if you want the Linux partition is as Drive1.  You could also replace /dev/sdb1 with the actual UUID of that partition which you can get by running:  sudo blkid.

---

### Post by Deucalion29710 on 2015-11-06
I made the directories, but I don't understand what you mean in the second part.  Is this exactly what I would add to fstab?

---

### Post by Deucalion29710 on 2015-11-06
> **yancek said:**
> A mount point is simply a directory so you would just use the terminal and create them.  The standard place to mount is the /mnt directory so:

```
sudo mkdir /mnt/Drive1
```

Repeat for Drive2.  For the Linux partition on sdb1 you could use:



That is, if you want the Linux partition is as Drive1.  You could also replace /dev/sdb1 with the actual UUID of that partition which you can get by running:  sudo blkid.

In other words would this be the correct way to edit fstab?:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=48457920-395c-4ec5-815e-65aa02a23bba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e38363c5-8c4a-4176-bf6c-acc56781c35c none            swap    sw              0       0
/dev/sdb1 /mnt/Drive1 ext4 errors=remount-ro 0 1
/dev/sdc1 /mnt/Drive2 ntfs errors=remount-ro 0 1

---

### Post by tturrisi on 2015-11-06
If use Gnome, in a terminal do:
sudo gedit /etc/fstab

add this to fstab at the bottom:
```
/dev/sdb1	/media/Drive1	ext4	rw,user,exec,umask=000	0	0
/dev/sdc1	/media/Drive2	ntfs-3g	defaults,uid=1000,gid=1000,umask=0000,fmask=0111	0	0
```

to mount immediately, in  a terminal do:
sudo mount -a

The drives should be mounted when booting.

If no joy, access the User-Group settings and add yourself to the fuse group.

---

