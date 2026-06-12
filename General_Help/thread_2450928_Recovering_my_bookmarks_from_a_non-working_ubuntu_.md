---
title: "Recovering my bookmarks from a non-working ubuntu instance"
date: 2020-09-23
forum: General Help
---

### Post by han-xiao on 2020-09-23
I have a dual boot windows 10 and xubuntu.

Ubuntu is on a separate drive which I want to remove and then my children can use this machine as windows only.

I have some bookmarks and data I would like to retrieve before removing the ubuntu drive.

I under stand this can be done using a live usb and have tried following guidance I found but I come unstuck when trying to mount the ubuntu system.

```

xubuntu@xubuntu:~$ sudo mkdir /rescue

```

```

xubuntu@xubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.42 GiB, 1510060032 bytes, 2949336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 223.58 GiB, 240057409536 bytes, 468862128 sectors
Disk model: OCZ-VECTOR180   
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 9EFB600C-A9FF-4A05-863B-84E383D8B32F

Device         Start       End   Sectors   Size Type
/dev/sda1       2048    487423    485376   237M EFI System
/dev/sda2     487424  40486911  39999488  19.1G Linux filesystem
/dev/sda3   40486912 464422911 423936000 202.2G Linux filesystem
/dev/sda4  464422912 468860927   4438016   2.1G Linux swap


Disk /dev/sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: TOSHIBA MQ02ABD1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: C79D48CD-4D4D-4DAA-A116-0A83EBA9B7EC

Device          Start        End    Sectors   Size Type
/dev/sdb1        2048      34815      32768    16M Microsoft reserved
/dev/sdb2       34816 1715957759 1715922944 818.2G Microsoft basic data
/dev/sdb3  1715957760 1953521663  237563904 113.3G Microsoft basic data


Disk /dev/sdc: 116.96 GiB, 125560421888 bytes, 245235199 sectors
Disk model: USB 3.0 FD      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x1421776c

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdc1        2048 245233663 245231616  117G  b W95 FAT32


Disk /dev/sdd: 14.6 GiB, 15664676864 bytes, 30595072 sectors
Disk model: Cruzer Blade    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x60596519

Device     Boot   Start      End  Sectors  Size Id Type
/dev/sdd1  *          0  3247999  3248000  1.6G  0 Empty
/dev/sdd2       3168916  3176851     7936  3.9M ef EFI (FAT-12/16/32)
/dev/sdd3       3248128 30595071 27346944   13G 83 Linux
xubuntu@xubuntu:~$

```

```

xubuntu@xubuntu:~$ sudo mount | grep ^/dev
/dev/sdd1 on /cdrom type iso9660 (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/dev/sdd3 on /var/log type ext4 (rw,relatime)
/dev/sdd3 on /var/crash type ext4 (rw,relatime)
/dev/sdb2 on /media/xubuntu/18A0935FA0934264 type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
xubuntu@xubuntu:~$

```

I can see that ubuntu is on /devsda2 from fdisk but it is not listed as mounted. When I try to mount it I get an error:

```

xubuntu@xubuntu:~$ sudo mount -t ext4 /dev/sda2
mount: /dev/sda2: can't find in /etc/fstab.
xubuntu@xubuntu:~$

```

Gparted shows me that the ubuntu system is at sda2, is ext4 and that the data files I need are at /sda3.

How can I mount the ubuntu system because apparently the next step is chroot.

---

### Post by ActionParsnip on 2020-09-23
Why do you not have them as part of your regular backups?

---

### Post by han-xiao on 2020-09-23
Because what I want was made after the last backup.

---

