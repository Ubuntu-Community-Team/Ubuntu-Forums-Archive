---
title: "mount /dev/md0 with normal user access"
date: 2015-08-06
forum: General Help
---

### Post by ozzie1 on 2015-08-06
I'm using Ubuntu MATE 15.04. I've created a software raid1 array using 2 3TB drives and parted/mdadm, config files below. This is intended to be a basic samba file server with remote ftp access capabilities. The problem is that at boot the array mounts as owned by root/root with read-only user access. How do I change this to either be owned by my normal user account (with rw permissions for a samba account) or to give access to other accounts? I used to know this, but it's been a while since I've used linux.

```
corey@pattern:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed Aug  5 19:16:33 2015
     Raid Level : raid1
     Array Size : 2930134016 (2794.39 GiB 3000.46 GB)
  Used Dev Size : 2930134016 (2794.39 GiB 3000.46 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Thu Aug  6 00:47:59 2015
          State : active, resyncing 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

  Resync Status : 29% complete

           Name : pattern:0  (local to host pattern)
           UUID : xxxx
         Events : 3204

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
corey@pattern:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--mate--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=xxxx /boot           ext2    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=xxxx  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/ubuntu--mate--vg-swap_1 none            swap    sw              0       0
/dev/md0 /media/md0 ext4 defaults 0 0
corey@pattern:~$ cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=corey group=corey mode=0660 auto=yes #this was changed after the initial creation of the array

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Wed, 05 Aug 2015 17:29:04 -0400
# by mkconf $Id$
ARRAY /dev/md0 metadata=1.2 UUID=xxxx

```

---

### Post by nerdtron on 2015-08-06
Have you tired creating a new folder inside the md0 folder, make it readable/writable to others and then create a samba share to the folder.

---

### Post by ozzie1 on 2015-08-06
That does work, but I'd prefer to have direct access to the root folder of the array, rather than doing everything through subfolders. I'm going to have to start over anyways, I forgot to leave space on the drives for a swap partition and log files (the main drive is a small SSD, to keep power consumption down when the drives aren't in use), is there anything I should do different? Is the CREATE line in mdadm.conf only used when the array is first created?

---

### Post by SeijiSensei on 2015-08-06
Give the mount point 777 permissions.
```
sudo chmod 777 /media/md0
```

I've never set any ownerships or permissions in mdadm.conf.  I usually just build the array as root, format it with "sudo mkfs -t ext4 /dev/md0", then mount it as root letting the mount point's permissions govern access to the array.

---

### Post by ozzie1 on 2015-08-06
> **SeijiSensei said:**
> Give the mount point 777 permissions.
```
sudo chmod 777 /media/md0
```


Huh, I tried that with the first array, got no errors but when I checked the permissions afterwards they'd reverted to the previous setting, chown did the same. This time chmod worked, didn't try chmod. Thanks!

---

