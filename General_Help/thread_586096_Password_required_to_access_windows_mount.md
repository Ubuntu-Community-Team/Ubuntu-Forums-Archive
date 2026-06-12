---
title: "Password required to access windows mount"
date: 2007-10-21
forum: General Help
---

### Post by Jacky_J on 2007-10-21
One nice thing ubuntu does is automatically add your fat32/ntfs partitions to fstab upon installation.  However, if you want to access them, you have to type in your password.

Is there a way to disable that and just open up access to it?

fstab output:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ccf4a0a4-1168-4be7-a53e-1db4d02e70db /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7274155a-7e29-4705-92cd-36942f66e4c3 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

fdisk -l output:
```

Disk /dev/sda: 159.9 GB, 159997493248 bytes
255 heads, 63 sectors/track, 19451 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c739c73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14228   114286378+   7  HPFS/NTFS
/dev/sda2           14229       15533    10482412+   c  W95 FAT32 (LBA)
/dev/sda3           15534       19284    30129907+  83  Linux
/dev/sda4           19285       19451     1341427+   5  Extended
/dev/sda5           19285       19451     1341396   82  Linux swap / Solaris

```

df -h output:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              29G  3.2G   24G  12% /
varrun               1014M   84K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   64K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda2              10G  4.9G  5.2G  49% /media/SHARE
/dev/sda1             109G   80G   30G  73% /media/disk

```

---

### Post by louieb on 2007-10-22
The  Windows type file system I see in you fdisk listing is sda1 (ntfs) and sda2 (fat32). Don't see them in /etc/fstab. 
Nice how to here: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Jacky_J on 2007-10-23
Cool, thanks for the link. It's a shame ubuntu doesn't do this by default.

I'm not sure why it didn't list those in fstab. Maybe ubuntu has some special startup script that mounts them automatically.

---

