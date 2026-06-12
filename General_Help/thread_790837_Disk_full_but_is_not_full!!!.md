---
title: "Disk full but is not full!!!"
date: 2008-05-11
forum: General Help
---

### Post by Ski-lleR on 2008-05-11
Hi

I recently installed ubuntu on my computer, after some day, i encounter a small problem (sorry i'm french, but on ubuntu france> no help).

I parted my hdd like this:
/         20 Gb
/home     55 Gb
/boot     100 Mb
swap      1 or 2 Gb (i don't know exactly)

Previously, i have 8 gb of free space in home (logically because my home is like my storage, now i know it's a bad idea, it's better to conserve home for configuration file, and create partition especially for storage).

But this day i can no more write/copy file, because ubuntu say "disk is full"

Check out df -h>

> jeremy@unknown-system:~$ df -h
Sys. de fich.            Tail. Occ. Disp. %Occ. Monté sur
/dev/sdb7              19G  4,3G   14G  25% /
varrun                252M   76K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   76K  252M   1% /dev
devshm                252M  112K  252M   1% /dev/shm
lrm                   252M   38M  215M  15% /lib/modules/2.6.24-17-generic/volatile
/dev/sdb6              89M   40M   45M  47% /boot
/dev/sdb8              55G   37G   15G  72% /home
gvfs-fuse-daemon       19G  4,3G   14G  25% /home/jeremy/.gvfs


du -h>
...some file
...some file
...some file
...some file
Total> 37G	/home

Gparted>
[IMG]http://img106.imageshack.us/img106/7072/capturedevsdbgpartedpx2.png[/IMG]

System monitor>
[IMG]http://img301.imageshack.us/img301/1152/capturemoniteursystme2ul3.png[/IMG]

Analyse tools>
[IMG]http://img403.imageshack.us/img403/3863/captureanalyseurdutiliswu8.png[/IMG]

- tried to delete 4 gb of data> no more help.
- tried to scan hdd with fsck > no more help.
- tried to clean trash > no more help
- tried to clean apt > no more help

Last example, i can't no more download amsn svn (no space...). For 2 minutes i've tried, tried, tried, and now i have succesfully downloaded amsn svn...after compil, i tried to download plugins, no more space...>

[IMG]http://img247.imageshack.us/img247/155/capturemi1.png[/IMG]

Beforce that i can't no more do screenshot, now i can...

We can see: 14 Go d'espace libre en bas (14 Gb of free space> bottom)

What's the hell ?

---

### Post by rogblake on 2008-05-11
Are you out of inodes? Try running "df -ih" to check this.

---

### Post by russo.mic on 2008-05-12
Just putting this out there, you shouldn't nearly 20 gigs for your / partition.  I usually give mine about 4 gigs.

Russo

---

### Post by Ski-lleR on 2008-05-12
Hi

First, thanks for the response.
russo.mic> Ok so i remember to reduce the / size ;)

rogblake> Out of inode ? what's this ? Apparently you're ok because used = 100%

> jeremy@unknown-system:~$ df -ih
Sys. de fich.            Inodes   IUtil.  ILib. %IUti. Monté sur
/dev/sdb7               1,2M    185K   1011K   16% /
varrun                   63K      43     63K    1% /var/run
varlock                  63K       1     63K    1% /var/lock
udev                     63K    3,1K     60K    5% /dev
devshm                   63K       3     63K    1% /dev/shm
lrm                      63K      18     63K    1% /lib/modules/2.6.24-17-generic/volatile
/dev/sdb6                48K      59     48K    1% /boot
/dev/sdb8                14K     14K      20  100% /home
gvfs-fuse-daemon        1,2M    185K   1011K   16% /home/jeremy/.gvfs

I try to find on google how change that, but if you come here (or another), say me how correct the problem

Thanks ;)

---

### Post by rogblake on 2008-05-12
> **Ski-lleR said:**
> Hi

First, thanks for the response.
rogblake> Out of inode ? what's this ? Apparently you're ok because used = 100%
Thanks ;)

Inodes are the on-disk data structures in traditional Unix-type filesystems that contain file characteristics. Just like on Unix systems, the inodes are statically allocated on Linux ext2 and ext3. When the filesystem is first created (that is, when the partition is formatted) a fixed number of inodes are created. It is usually a sufficient amount, but every time you create a file or a hard link an inode is used up, so it is possible to run out of inodes if you have lots and lots of files. 

Unfortunately I don't think it is possible to change the inode allocation once the filesystem is created. What you would need to do is backup the filesystem, then use "mkfs.ext3" or "mkfs -t ext3" to recreate it. If the default setting doesn't give you enough inodes, you can use the "-N' option to specify how many you want. Then restore your backup.

It looks to me like your /home partition has an unusually small number of inodes allocated. You're showing only 14K inodes for the entire partition! (For comparison, one of my Linux systems has a 138GB /home partition and 18M of inodes, only 270K of which are in use.)

---

### Post by timcredible on 2008-05-12
first, what disk (partition) is it saying is full?

also, what is /boot?  whatever it is, it's only got 4MB of space? 

you might want to re-install, with no /boot partition, about 10-15GB for /, keep the 1.5GB for swap, and the rest for /home.

---

