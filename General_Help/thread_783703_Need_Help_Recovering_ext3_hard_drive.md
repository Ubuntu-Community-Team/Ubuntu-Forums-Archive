---
title: "Need Help Recovering ext3 hard drive"
date: 2008-05-06
forum: General Help
---

### Post by Polygon on 2008-05-06
so my comp crahsed, and when i rebooted, i noticed my usb hard drive wasnt mounting anymore. Then to my horror gparted says the filesystem is 'unallocated' instead of ext3

i ran fsck on it but this is what its saying:
> 
mark@Aurora:~$ sudo fsck /dev/sdd
[sudo] password for mark: 
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdd

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


How do i repair the filesystem and get my stuff back?

---

### Post by Polygon on 2008-05-06
actually, i unplugged and plugged the drive backl in, and gparted suddenly saw the drive as ext3. I then just right clicked > repair and did that, and now it mounts normally. yay

---

### Post by amohanty on 2008-05-06
sudo fsck -r /dev/sdd

hth
am

---

