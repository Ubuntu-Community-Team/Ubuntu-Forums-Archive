---
title: "File size caped at 1.7 G?"
date: 2008-06-11
forum: General Help
---

### Post by Merc84TD on 2008-06-11
Im trying to install world of warcraft using wine. But all of the folders im trying to install too are limited to 1.7 gigs. Is there a way to change this, and if so could someone walk me through it? Thanks

---

### Post by KingTermite on 2008-06-11
Don't know the solution...but found a tutorial that may  help.

[http://gentoo-wiki.com/World_Of_Warcraft/Wine](http://gentoo-wiki.com/World_Of_Warcraft/Wine)


Wine Ref: [http://appdb.winehq.org/appview.php?iAppId=1922](http://appdb.winehq.org/appview.php?iAppId=1922)

---

### Post by Dylock on 2008-06-11
Whats the file system of the partition you are trying to install to?
You can find this out by using

```
df -T 
```

or

```
mount
```

Once you figure out what file system you have you can find out what the maximum filesize for that file system is. (Granted you would have to be using some strange file system to have a max size around 1.7GB but hey it's a start)

---

### Post by Merc84TD on 2008-06-12
When i type df -T I get
 kyle@comp:~$ df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sdb2     ext3     5044188   3127252   1660700  66% /
varrun       tmpfs     1557432        84   1557348   1% /var/run
varlock      tmpfs     1557432         0   1557432   0% /var/lock
udev         tmpfs     1557432       116   1557316   1% /dev
devshm       tmpfs     1557432         0   1557432   0% /dev/shm
lrm          tmpfs     1557432     34696   1522736   3% /lib/modules/2.6.22-14-generic/volatile
/dev/sdc2     vfat    29207952  22418064   6789888  77% /media/KYLE'S IPOD
/dev/scd0      udf     4076768   4076768         0 100% /media/cdrom0
/dev/sda2  fuseblk   151316232 110415180  40901052  73% /media/disk-1
/dev/sdb1  fuseblk   307154732 115939548 191215184  38% /media/disk-2
kyle@comp:~$ 

media disk 1 is a 130g hd with xp on it, and midia disk 2 is 260g hd with ubuntu installed on it. I have partitioned they entire media disk 2 for ubuntu

i would like to install it to /home/kyle/documents but it says that there is only 1.7g of free space

---

### Post by plucky on 2008-06-12
> /dev/sdb2 ext3 5044188 3127252 1660700 66% /

That is your /root partition and you only have 1.66G available


Try ```
df -h
```
and ```
sudo fdisk -l
``` lowercase L not a 1

---

### Post by Merc84TD on 2008-06-12
kyle@comp:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             4.9G  2.9G  1.7G  64% /
varrun                1.5G   88K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  100K  1.5G   1% /dev
devshm                1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G   34M  1.5G   3% /lib/modules/2.6.22-14-generic/volatile
/dev/scd0             3.9G  3.9G     0 100% /media/cdrom0
/dev/sda2             145G  106G   40G  73% /media/disk-1
/dev/sdb1             293G  111G  183G  38% /media/disk-2
kyle@comp:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       18845   151316235    7  HPFS/NTFS
/dev/sda3           18847       19452     4867695   db  CP/M / CTOS / ...

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00073ab4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38239   307154736    7  HPFS/NTFS
/dev/sdb2   *       38240       38877     5124735   83  Linux
/dev/sdb3           38878       38913      289170    5  Extended
/dev/sdb5           38878       38913      289138+  82  Linux swap / Solaris
kyle@comp:~$ 



Is there any way to make the root folder bigger? If you couldn't tell, im rather new to ubuntu. :-)

---

### Post by plucky on 2008-06-12
> Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00073ab4

Device Boot Start End Blocks Id System
/dev/sdb1 1 38239 307154736 7 HPFS/NTFS
/dev/sdb2 * 38240 38877 5124735 83 Linux
/dev/sdb3 38878 38913 289170 5 Extended
/dev/sdb5 38878 38913 289138+ 82 Linux swap / Solaris


You could shrink your /dev/sdb1 partition which is 307G and give some of it to Ubuntu.

If you are using vista,it is best to use vista disk management to shrink the partition.

If you are using XP then you can use the Partition editor on the live CD or download an burn the [Gparted Live CD](http://gparted.sourceforge.net/) to resize the XP and Ubuntu partition.


Good Luck

---

### Post by Merc84TD on 2008-06-14
I was able to fix it by formatting the HD using whatever partitioning tool comes with XP. Then I reinstalled Ubuntu. It fixed this problem, and several others i was having too. Thanks for your help everyone.

---

