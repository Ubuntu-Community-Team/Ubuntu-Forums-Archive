---
title: "LVM Partition being detected wrong size."
date: 2015-04-27
forum: General Help
---

### Post by ausrick1 on 2015-04-27
Hello Everyone,

There is a server I'm responsible for that is showing a drive (full) and much smaller than the drive should be. My knowledge of LVM is not deep enough to see why. I could use some help from a good fresh set of eyes because I've been scratching (and banging) my head on this.

I have a Logical Volume /dev/sdrive/shared which is 352 GiB. My OS, Ubuntu 14.04.01, seems to only think /dev/mapper/sdrive-shared is 126G. I don't know what I screwed up or did wrong to cause this or how to fix it. Below I'm including the output of what commands I know to investigate the problem. I don't see where it's getting the 126G from though. 

Some things seem like errors to me (like fdisk complaining about a partition table, but parted showing fine) but searching some forums say this is expected behavior when it comes to LVM. Again, my knowledge is too weak to diagnose and I am grasping at straws and appreciate any help. thanks! 

```

login as: itdept
itdept@192.168.0.92's password:
Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-49-generic i686)


 * Documentation:  https://help.ubuntu.com/


  System information as of Mon Apr 27 08:45:41 EDT 2015


  System load:  0.0                Processes:           109
  Usage of /:   18.1% of 34.82GB   Users logged in:     1
  Memory usage: 3%                 IP address for eth0: 192.168.0.92
  Swap usage:   0%


  => /srv/shared is using 100.0% of 125.87GB


  Graph this data and manage this system at:
    https://landscape.canonical.com/


Last login: Mon Apr 27 08:45:45 2015 from 192.168.0.84
itdept@SFTP-SVR:~$ sudo su
[sudo] password for itdept:
root@SFTP-SVR:/home/itdept# pvdisplay
  --- Physical volume ---
  PV Name               /dev/xvdc1
  VG Name               sdrive
  PV Size               384.00 GiB / not usable 3.00 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              98303
  Free PE               8191
  Allocated PE          90112
  PV UUID               xeWJim-n58M-hvzd-3DbA-Nlgz-d3l1-e7IiG7


root@SFTP-SVR:/home/itdept# vgdisplay
  --- Volume group ---
  VG Name               sdrive
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  5
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               384.00 GiB
  PE Size               4.00 MiB
  Total PE              98303
  Alloc PE / Size       90112 / 352.00 GiB
  Free  PE / Size       8191 / 32.00 GiB
  VG UUID               UsISz5-zVvV-HnQe-5szT-mgxr-qrql-tlCU3J
  
root@SFTP-SVR:/home/itdept# lvdisplay
  --- Logical volume ---
  LV Path                /dev/sdrive/shared
  LV Name                shared
  VG Name                sdrive
  LV UUID                MoIYg0-XhWd-t931-U7Tz-5hw8-YDDr-qXUfkb
  LV Write Access        read/write
  LV Creation host, time SFTP-SVR, 2014-09-15 18:02:18 -0400
  LV Status              available
  # open                 1
  LV Size                352.00 GiB
  Current LE             90112
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0


root@SFTP-SVR:/home/itdept# df -h
Filesystem                                  Size  Used Avail Use% Mounted on
/dev/xvda1                                   35G  6.4G   27G  20% /
none                                        4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                        2.0G  4.0K  2.0G   1% /dev
tmpfs                                       404M  236K  404M   1% /run
none                                        5.0M     0  5.0M   0% /run/lock
none                                        2.0G     0  2.0G   0% /run/shm
none                                        100M     0  100M   0% /run/user
/dev/mapper/sdrive-shared                   126G  126G     0 100% /srv/shared
192.168.0.201:/mnt/HD/HD_a2                 732G  187G  546G  26% /mnt/ShareCenter
172.29.0.5:/mnt/UVB-CITRIX-01/Rdiff-Backup  8.7T  357G  8.4T   5% /mnt/RdiffBackup


root@SFTP-SVR:/home/itdept# parted -l
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/sdrive-shared: 378GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  378GB  378GB  ext4




Model: Xen Virtual Block Device (xvd)
Disk /dev/xvda: 38.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  38.1GB  38.1GB  primary   ext4
 2      38.1GB  38.7GB  535MB   extended
 5      38.1GB  38.7GB  535MB   logical   linux-swap(v1)




Error: /dev/xvdb: unrecognised disk label


Model: Xen Virtual Block Device (xvd)
Disk /dev/xvdc: 550GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  481GB  481GB  primary               lvm




root@SFTP-SVR:/home/itdept# fdisk -l


Disk /dev/xvda: 38.7 GB, 38654705664 bytes
255 heads, 63 sectors/track, 4699 cylinders, total 75497472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003ec0e


    Device Boot      Start         End      Blocks   Id  System
/dev/xvda1            2048    74448895    37223424   83  Linux
/dev/xvda2        74450942    75495423      522241    5  Extended
/dev/xvda5        74450944    75495423      522240   82  Linux swap / Solaris


Disk /dev/xvdc: 549.8 GB, 549755813888 bytes
64 heads, 1 sectors/track, 16777216 cylinders, total 1073741824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1f2d154a


    Device Boot      Start         End      Blocks   Id  System
/dev/xvdc1            2048   939526143   469762048   8e  Linux LVM


Disk /dev/xvdb: 268.4 GB, 268435456000 bytes
255 heads, 63 sectors/track, 32635 cylinders, total 524288000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/xvdb doesn't contain a valid partition table


Disk /dev/mapper/sdrive-shared: 378.0 GB, 377957122048 bytes
255 heads, 63 sectors/track, 45950 cylinders, total 738197504 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/sdrive-shared doesn't contain a valid partition table




root@SFTP-SVR:/home/itdept# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/xvda1 during installation
UUID=1ad70e2c-38b8-4c71-937a-36e1775ccc10 /               ext4    errors=remount-ro 0       1
# swap was on /dev/xvda5 during installation
UUID=e4d98211-c0f2-4b97-ab88-28e52e47b5f1 none            swap    sw              0       0
# ShareCenter NFS
192.168.0.201:/mnt/HD/HD_a2 /mnt/ShareCenter nfs defaults,rw,auto 0 0
# RdiffBackup on SAM-SD NFS for Backups
172.29.0.5:/mnt/UVB-CITRIX-01/Rdiff-Backup /mnt/RdiffBackup nfs defaults,auto,rw 0 0
# shared for sdrive (LVM, ext4)
/dev/sdrive/shared /srv/shared ext4 rw,noatime,auto 0 0

```

---

### Post by ausrick1 on 2015-05-08
I'm not sure why no replies? Anyway, I was able to find help elsewhere and will share for anyone searching for this. The issue was that at one time the partition was enlarged and the filesystem needed to be extended to match with the resize2fs command:

```

root@SFTP-SVR:/home/itdept# resize2fs /dev/sdrive/shared
resize2fs 1.42.9 (4-Feb-2014)
Filesystem at /dev/sdrive/shared is mounted on /srv/shared; on-line resizing required
old_desc_blocks = 8, new_desc_blocks = 22
The filesystem on /dev/sdrive/shared is now 92274688 blocks long.


root@SFTP-SVR:/home/itdept# df -h
Filesystem                                  Size  Used Avail Use% Mounted on
/dev/xvda1                                   35G  8.6G   25G  26% /
none                                        4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                        2.0G   12K  2.0G   1% /dev
tmpfs                                       404M  252K  404M   1% /run
none                                        5.0M     0  5.0M   0% /run/lock
none                                        2.0G     0  2.0G   0% /run/shm
none                                        100M     0  100M   0% /run/user
/dev/mapper/sdrive-shared                   347G  126G  206G  39% /srv/shared
192.168.0.201:/mnt/HD/HD_a2                 732G  187G  546G  26% /mnt/ShareCenter
172.29.0.5:/mnt/UVB-CITRIX-01/Rdiff-Backup  7.3T  360G  7.0T   5% /mnt/RdiffBackup
root@SFTP-SVR:/home/itdept#

```

---

