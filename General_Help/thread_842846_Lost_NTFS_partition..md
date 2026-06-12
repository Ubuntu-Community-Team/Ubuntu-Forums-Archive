---
title: "Lost NTFS partition."
date: 2008-06-27
forum: General Help
---

### Post by Raws on 2008-06-27
Hello, fellows

Fist of all let me clarify that 1. I´m completely noob in linux (Made my first install of ubuntu 8.04 2 days ago) 2. I'm brazilian, so english is not my first language 3. This is my first post, in the forum.

That said, please be patient with me and forgive any rubish I eventualy say.

Going to my problem.

I have two 500GB hds, both previosly formatted in NTFS, by Window$ Vista, witch remained instaled in one of them.

To make my transition to Linux easier I decided to install Ubuntu in the 2nd harddrive.

I reduced the NTFS partition in HD2 by 52GB, left 2 for swap and 50 to linux and the remaining 448GB was left still in one NTFS partition, with about 230GB of data mixing music, videos, documents and other files...

I used this harddrive as the booting (the boot is on sdb1)

After installing ubuntu it imediately recognised sda1 (the 500GB Window$ vista HD) and sdb5 (Ubuntu) and sdb6 (swap) BUT it didnt mount sdb1 (the 448GB NTFS partition with about 230GB of data).

I tried to mount the partition in Ubuntu without sucess. Gparted recognises the partition as boot, but I cant access any of its contents.
 
Worse, I tried to boot in Window$ Vista and it also didn't recognize de partition, saying it is not formatted.

I tried to boot with Window$ XP and running ontrack easyrecovery, it didnt work.

Anybody knows how (or IF) I can recover the data?

Assuming its lost, is there a way to make all the harddrive into a linux partition without losing my actual installation of Ubuntu or the booting?

My configuration is:
C2D e4500
Asus P5K SE
ECS GF 8800GT
2GB RAM
2 500GB HDs => sda1 with Win Vista / sdb with boot (NTFS lost data) Ubuntu 8.04 and swap.

Sorry for any misspeling, and thanks a lot for any help.

---

### Post by russlar on 2008-06-27
I doubt it's lost. Try fdisk -l, this will list all of the hard drives that your PC can see. df -h will list all hard drives that are mounted, those that are not already mounted, you can use mount to manually mount.

---

### Post by Raws on 2008-06-27
Russlar, thaks for the tip, but it didnt work.

See what i've done:

raul@raul-pc:~$ sudo fdisk -l
[sudo] password for raul: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13d413d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
48 heads, 46 sectors/track, 442379 cylinders
Units = cylinders of 2208 * 512 = 1130496 bytes
Disk identifier: 0x144f144e

[B]   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      396002   437184512    7  HPFS/NTFS
/dev/sdb2          396003      442379    51200208    5  Extended
/dev/sdb5          398152      442379    48827712   83  Linux
/dev/sdb6          396003      398150     2371346   82  Linux swap / Solaris
[/B]
Partition table entries are not in disk order
raul@raul-pc:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5              47G  9.2G   35G  21% /
varrun               1014M  108K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   52K 1014M   1% /dev
devshm               1014M  188K 1014M   1% /dev/shm
lrm                  1014M   38M  977M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       47G  9.2G   35G  21% /home/raul/.gvfs
/dev/sda1             466G  403G   64G  87% /media/disk
[B]raul@raul-pc:~$ sudo mount -t ntfs /dev/sdb1 /media/disk2
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
raul@raul-pc:~$ 
[/B]

Any other thoughts??

---

