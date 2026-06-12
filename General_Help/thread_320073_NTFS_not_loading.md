---
title: "NTFS not loading"
date: 2006-12-16
forum: General Help
---

### Post by Robbyx on 2006-12-16
I am struggling to see what I am doing wrong, but when I try to mount the drives with 

sudo mount -a

instead of mounting I have the following error messages:

mount: mount point /media/f does not exist
mount: mount point /media/h does not exist
mount: mount point /media/i does not exist

I have tried rebooting but it made no difference.

I have created new directories of f, h, and I below media with the command:
sudo mkdir /media/F
ditto for h and i

this is the results of fdisk -l

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        8923    30716280   83  Linux
/dev/sda3            8924        9433     4096575   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100        8923    30716280   83  Linux
/dev/sdb3            8924        9433     4096575   82  Linux swap / Solaris

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+  83  Linux
/dev/hda2           14217       14593     3028252+   5  Extended
/dev/hda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1            2708        5005    18458685    f  W95 Ext'd (LBA)
/dev/hdb5            2708        3699     7968208+   7  HPFS/NTFS
/dev/hdb6            3700        4591     7164958+   7  HPFS/NTFS
/dev/hdb7            4592        5005     3325423+   7  HPFS/NTFS
robin@robin-desktop:~$ 
```





This is my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5c72cd85-be0f-44f5-b399-1d3361b8e385 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=5abbef3f-03f4-4927-868f-93ec33fe1a6f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

#new lines added to enable mounting of ntfs drives
/dev/hdb5     /media/f    ntfs     nls=utf8,umask=0222 0 0
/dev/hdb6     /media/h    ntfs     nls=utf8,umask=0222 0 0
/dev/hdb7     /media/i    ntfs     nls=utf8,umask=0222 0 0

# The following did not work and was changed to above as per
# http://www.psychocats.net/ubuntu/mountwindows
# /dev/hdb5     /media/f    ntfs-3g     defaults,locale=en_US.utf8   0    0
# /dev/hdb6     /media/h    ntfs-3g     defaults,locale=en_US.utf8   0    0
# /dev/hdb7     /media/i    ntfs-3g     defaults,locale=en_US.utf8   0    0

```


Robin

---

### Post by taurus on 2006-12-16
Linux is case sensitive so /media/f _IS NOT THE SAME AS_ /media/F...

```
sudo mkdir /media/f /media/h /media/i
sudo mount -a
df -h
```

---

### Post by zappa420 on 2006-12-16
sudo mount -t ntfs-3g /dev/hdb5 /media/f
sudo mount -t ntfs-3g /dev/hdb6 /media/h
sudo mount -t ntfs-3g /dev/hdb7 /media/i

Thats how I would do it, 'less you want them loaded everytime you boot.  Then you need to edit fstab.

---

### Post by Robbyx on 2006-12-17
Thank you both for your replies. I can see that I have not matched the drive case. I hope it will now work. I will make the changes and see what happens.

Robin

---

