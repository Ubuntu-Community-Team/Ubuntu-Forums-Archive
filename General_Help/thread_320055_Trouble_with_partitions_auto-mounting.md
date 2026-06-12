---
title: "Trouble with partitions auto-mounting"
date: 2006-12-16
forum: General Help
---

### Post by damoek on 2006-12-16
Hello.
I finally decided to upgrade my NTFS drive to Ext3 because I am tired of all of my files not having write access. So I backed up all the files and partitioned my 250gb drive into 5 50gb partitions. I edited /etc/fstab to reference all of the partitions on /dev/sdb to have them auto mount and I can not access the files through nautilus or the command line with sudo mount -a

I formatted the partitions with sudo mke2fs -j /dev/sdb

here is my /etc/fstab file
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7 -- converted during upgrade to edgy
UUID=47fd1ff9-1555-431b-bdfb-6e34ad611eca / ext3 defaults,errors=remount-ro 0 1
# /dev/sda2 -- converted during upgrade to edgy
UUID=B8EC267AEC263354 /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=b807280b-0700-47a7-abfc-bca7fb64fa84 /media/sda5 ext3 defaults 0 2
# /dev/sdb1 /media/sdb1 ext3 defaults 0 2
# /dev/sdb2 /media/sdb2 ext3 defaults 0 0
# /dev/sdb3 /media/sdb3 ext3 defaults 0 0
# /dev/sdb4 /media/sdb4 ext3 defaults 0 0
# /dev/sdb5 /media/sdb5 ext3 defaults 0 0
# /dev/sdb6 /media/sdb6 ext3 defaults 0 0
# /dev/sda6 -- converted during upgrade to edgy
UUID=7c386acd-7d64-42ce-aae1-44c2d2795961 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


and here is the output of fdisk -l
> 
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        5099    40949685    f  W95 Ext'd (LBA)
/dev/sda2   *        5100       24321   154400715    7  HPFS/NTFS
/dev/sda5               2        2551    20482843+   7  HPFS/NTFS
/dev/sda6            2552        2682     1052226   82  Linux swap / Solaris
/dev/sda7            2683        5099    19414521   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6527    52428096   83  Linux
/dev/sdb2            6528       13054    52428127+  83  Linux
/dev/sdb3           13055       19581    52428127+  83  Linux
/dev/sdb4           19582       30515    87827355    5  Extended
/dev/sdb5           19582       24834    42194691   83  Linux
/dev/sdb6           24835       30515    45632601   83  Linux


can someone point me in the right direction? 

Thanks.

---

### Post by taurus on 2006-12-16
How come you comment them all out in /etc/fstab!!!  If you want to mount them, you need to remove the # in front of them and change the last value from 0 to 1...

```

/dev/sdb1 /media/sdb1 ext3 defaults 0 1
/dev/sdb2 /media/sdb2 ext3 defaults 0 1
/dev/sdb3 /media/sdb3 ext3 defaults 0 1
# /dev/sdb4 /media/sdb4 ext3 defaults 0 1
# You CANNOT mount /dev/sdb4 since it's an extended partition...
/dev/sdb5 /media/sdb5 ext3 defaults 0 1
/dev/sdb6 /media/sdb6 ext3 defaults 0 1

```

---

### Post by damoek on 2006-12-16
Thats the way that it was by default? 
If they are all commented out then it must be getting the configuration information from another file? Does Edgy use something different? I'll remove comments and reboot... thanks.

---

