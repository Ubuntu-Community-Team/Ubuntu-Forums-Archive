---
title: "luckybackup root help needed with mounting files"
date: 2015-03-12
forum: General Help
---

### Post by dtree46 on 2015-03-12
[ATTACH=CONFIG]260584[/ATTACH]

See attached photo.
How is this file mounted?
Attempting to mount says it is not listed in /etc/fstab.

dlw

---

### Post by nerdtron on 2015-03-12
Do you have a backup drive connected to the computer?
If you do, you just need to mount your hard drive to the correct mountpoint ask by lucky backup.

post the ouput of the following commands here:
```
lsblk
sudo fdisk -l
df -h

```

---

### Post by dtree46 on 2015-03-12
dlw@dlw-HP:~$ lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                         8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1                      8:1    0   243M  0 part 
&#9500;&#9472;sda2                      8:2    0     1K  0 part 
&#9492;&#9472;sda5                      8:5    0 931.3G  0 part 
  &#9500;&#9472;dlw--vg-root (dm-0)   252:0    0 927.5G  0 lvm  /
  &#9492;&#9472;dlw--vg-swap_1 (dm-1) 252:1    0   3.8G  0 lvm  [SWAP]
sdb                         8:16   1  14.9G  0 disk 
&#9492;&#9472;sdb1                      8:17   1  14.9G  0 part /media/dlw/16GB
sdc                         8:32   0 232.9G  0 disk 
&#9492;&#9472;sdc1                      8:33   0 215.2G  0 part /media/dlw/BKUP
sr0                        11:0    1  1024M  0 rom  
dlw@dlw-HP:~$ sudo fdisk -l
[sudo] password for dlw: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00059fd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
/dev/sda5          501760  1953523711   976510976   8e  Linux LVM

Disk /dev/mapper/dlw--vg-root: 995.9 GB, 995874570240 bytes
255 heads, 63 sectors/track, 121074 cylinders, total 1945067520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/dlw--vg-root doesn't contain a valid partition table

Disk /dev/mapper/dlw--vg-swap_1: 4022 MB, 4022337536 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/dlw--vg-swap_1 doesn't contain a valid partition table

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43c7d366

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   451280895   225639424   83  Linux

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029190

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    31266815    15632384    c  W95 FAT32 (LBA)
dlw@dlw-HP:~$ df -h
Filesystem                Size  Used Avail Use% Mounted on
/dev/mapper/dlw--vg-root  913G  6.5G  860G   1% /
none                      4.0K     0  4.0K   0% /sys/fs/cgroup
udev                      1.8G   12K  1.8G   1% /dev
tmpfs                     371M  1.3M  369M   1% /run
none                      5.0M     0  5.0M   0% /run/lock
none                      1.9G  148K  1.9G   1% /run/shm
none                      100M   56K  100M   1% /run/user
/dev/sdb1                  15G   12G  3.1G  80% /media/dlw/16GB
/dev/sdc1                 212G  961M  200G   1% /media/dlw/BKUP
dlw@dlw-HP:~$

---

### Post by nerdtron on 2015-03-13
Your drive is mounted on /media/dlw/BKUP. Do you have a Documents folder inside that? or You can try unmouting the drive and re mount it on /media/dlw/BKUP/Documents which is what luckybackup looks for.

```
sudo umount /dev/sdc1
sudo mkdir /media/dlw/BKUP/Documents
sudo chown dlw.dlw /media/dlw/BKUP/Documents
sudo mount /dev/sdc1 /media/dlw/BKUP/Documents

```

Then try lucky backup again.

---

### Post by dtree46 on 2015-03-13
Thank you!!! It worked. Thanks again.
dlw

---

