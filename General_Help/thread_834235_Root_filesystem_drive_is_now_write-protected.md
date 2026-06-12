---
title: "Root filesystem drive is now write-protected"
date: 2008-06-19
forum: General Help
---

### Post by biggunks on 2008-06-19
I can't seem to create any new files on my / and can't do simple commands such as passwd.

I found some advice to run the following, but as you can see that failed also.  It seems I'm stuck with my drive mounting as read only.  I'm running Hardy.

$sudo mount -o remount,rw /
mount: block device /dev/sdc1 is write-protected, mounting read-only

Here's the info from fdisk and file -s for the drive in question.

[INDENT]
$ sudo fdisk -l /dev/sdc

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris
$ sudo fdisk -l /dev/sdc1

Disk /dev/sdc1: 76.7 GB, 76717154304 bytes
255 heads, 63 sectors/track, 9326 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc1 doesn't contain a valid partition table
$ sudo fdisk -l /dev/sdc2
$ sudo fdisk -l /dev/sdc5

Disk /dev/sdc5: 3306 MB, 3306530304 bytes
255 heads, 63 sectors/track, 401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc5 doesn't contain a valid partition table
$ sudo file -s /dev/sdc1
/dev/sdc1: Linux rev 1.0 ext3 filesystem data (needs journal recovery) (errors) (large files)
$ sudo file -s /dev/sdc2
/dev/sdc2: x86 boot sector, extended partition table (last)\011
$ sudo file -s /dev/sdc5
/dev/sdc5: Linux/i386 swap file (new style) 1 (4K pages) size 807257 pages[/INDENT]

Here's the fdisk info for my other 2 drives.  I don't think you'll need it, but here it is anyways.

[INDENT]
$ sudo fdisk -l /dev/sda

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004bb3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux
$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12159    97667136   83  Linux
/dev/sdb2           12160       24318    97667167+  83  Linux
[/INDENT]

One other tidbit of info that might help is that after a power outage the other day, my drives seem to be mounting at different points.  For example, my /dev/sdc (the drive that I'm having trouble with), I think used to be /dev/hdd.  And I've had to recreate some of my symlinks.
[INDENT]
$ less /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=ff7ccb24-0212-4208-bf6a-f1c32f39ed3a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=5d0bfc71-1f98-4094-b6e7-3865d7d51a23 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

#
/dev/sda1       /mnt/sda1       auto    defaults        0       0
/dev/sdb1       /mnt/sdb1       auto    defaults        0       0
/dev/sdb2       /mnt/sdb2       auto    defaults        0       0
/dev/sdc1       /mnt/sdc1       auto    defaults        0       0
/dev/sdc2       /mnt/sdc2       auto    defaults        0       0
[/INDENT]

I appreciate the help.

---

### Post by justleen on 2008-06-19
get rid of the auto option on the harddrives, and add a FS type

try to mount a disk by hand, with ```
sudo  mount /dev/sdc1 /mnt/sdc1
```

your fstab should look this (im using lvm, but you should use the /dev/xxx):

/dev/lvm_main/root      /                       ext3    defaults        1 1
/dev/sda1               /data1                  ext3    defaults        1 2
/dev/lvm_main/home      /home                   ext3    defaults        1 2
/dev/lvm_main/opt       /opt                    ext3    defaults        1 2
/dev/lvm_main/tmp       /tmp                    ext3    defaults        1 2
/dev/lvm_main/usr       /usr                    ext3    defaults        1 2
/dev/lvm_main/usr.local /usr/local              ext3    defaults        1 2
/dev/lvm_main/var       /var                    ext3    defaults        1 2
/dev/lvm_main/var.tmp   /var/tmp                ext3    defaults        1 2

---

### Post by bodhi.zazen on 2008-06-19
Your file system is likely damaged and thus mounted ro

Boot a live CD (you can not run fsck on a mounted partition) and run :

```
fsck -rfv /dev/sdxy
```

where /dev/sdxy == your ubuntu root partition (/dev/sdb1 I think)

---

### Post by sdennie on 2008-06-19
You can also force a check on a particular partition by manually setting its mount count to 30 or more.  For example, to force a check on /dev/sda1 on next reboot:

```

sudo tune2fs -C 30 /dev/sda1

```

When you next reboot a check should be run before the fs is mounted read/write.

---

### Post by biggunks on 2008-06-19
You guys are awesome.  Buy yourselves a cup of coffee for me.

When I get home tonight, I'll pop the live cd in, run the fsck, and take a look at my fstab again.  Hopefully all will be good again.

---

### Post by tipiglen on 2008-07-04
Tried fsck from live cd

```


ubuntu@ubuntu:~$ sudo fsck -rfv /dev/sda3
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  162417 inodes used (9.58%)
    7907 non-contiguous inodes (4.9%)
         # of inodes with ind/dind/tind blocks: 19107/445/0
 3514095 blocks used (51.83%)
       0 bad blocks
       1 large file

  129299 regular files
   15777 directories
      69 character device files
      26 block device files
       2 fifos
     465 links
   17209 symbolic links (16138 fast symbolic links)
      26 sockets
--------
  162873 files
ubuntu@ubuntu:~$

```
Rebooted from hdd and still got a read-only filesystem.  I can write to it as su, or sudo, but it's just not comfortable....

Any ideas?

---

### Post by bodhi.zazen on 2008-07-05
Is the partition full ?

Run ```
df -h
```

Or to see just the root partition :

```
df -h | egrep /$
```

---

### Post by tipiglen on 2008-07-05
bodhi,   Namaste

Thanks for your reply.  still no joy.
> Is the partition full ?
here's the result:

```
ed@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              26G   14G   11G  57% /
varrun                252M  108K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   68K  252M   1% /dev
devshm                252M   52K  252M   1% /dev/shm
lrm                   252M   38M  214M  16% /lib/modules/2.6.24-19-generic/volatile
/dev/sda2             9.9G  4.5G  5.5G  45% /media/disk-6
gvfs-fuse-daemon       26G   14G   11G  57% /home/ed/.gvfs
/dev/sdb1             5.4G  335M  5.1G   7% /media/My Book
/dev/sdb3             156G   47G  101G  32% /media/disk-4
/dev/sdb4              59G  944M   58G   2% /media/disk-5
/dev/sdb2              79G   39G   40G  50% /media/disk-7
ed@ubuntu:~$ df -h | egrep /$
/dev/sda3              26G   14G   11G  57% /
ed@ubuntu:~$ 
```
The only thought I have is that it might be because I tried to have the windows partition open at boot via fstab.  Here's fstab as presently working with the 'offending'line commented out.  I'll comment out the other partition as well and reboot to see if that gives any joy.
```
ed@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f62e3f18-02e0-486f-b46a-54a67f105f08 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=d3dd670e-5b93-4d68-a2de-445b5a31e3ec none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# hopefully this will get share partition mounted at boot
/dev/sda2 /media/disk-6 vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
# same for windows partition mounted at boot
#/dev/sda1 /media/25_02_42_ fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
ed@ubuntu:~$
```

Thanks again.  System working fine otherwise.

Salaam/Shalom/Shanthi/Dorood/Peace
ed

---

### Post by vanadium on 2008-07-05
What is all this about? It is perfectly normal that you cannot write to the root directory (/) as a normal user. Moerover, there is no reason for you to write in the /

The output of your fsck indicates that your drive is in a perfect state.

In conclusion, you do not have any problem. Please do not attempt to create one.

---

### Post by chrisccoulson on 2008-07-05
> **vanadium said:**
> What is all this about? It is perfectly normal that you cannot write to the root directory (/) as a normal user. Moerover, there is no reason for you to write in the /

The output of your fsck indicates that your drive is in a perfect state.

In conclusion, you do not have any problem. Please do not attempt to create one.

If you look at the first post again, you will see this is not a prtitions problem. The drive is being remounted read-only for some reason

biggunks - Could you please post the output of:
```
ls -l /dev/disk/by-uuid/
```
That's just so we can make sure you ran fsck on the right volume.

---

### Post by Gunman1982 on 2008-07-05
Uhm I am a little bit confused, because:

> **biggunks said:**
> I can't seem to create any new files on my / and can't do simple commands such as passwd.

I found some advice to run the following, but as you can see that failed also.  It seems I'm stuck with my drive mounting as read only.  I'm running Hardy.

$sudo mount -o remount,rw /
mount: block device **/dev/sdc1** is write-protected, mounting read-only

...

# **/dev/hdb1**
UUID=ff7ccb24-0212-4208-bf6a-f1c32f39ed3a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=5d0bfc71-1f98-4094-b6e7-3865d7d51a23 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

#
/dev/sda1       /mnt/sda1       auto    defaults        0       0
/dev/sdb1       /mnt/sdb1       auto    defaults        0       0
/dev/sdb2       /mnt/sdb2       auto    defaults        0       0
/dev/sdc1       /mnt/sdc1       auto    defaults        0       0
/dev/sdc2       /mnt/sdc2       auto    defaults        0       0
[/INDENT]

I appreciate the help.

your /dev/hdb1 should be your root but it complains about /dev/sdc1. So where exactly are you trying to write as your normal user? in your /home/user/ directory (where you should be allowed to write) or somewhere else (where you are not allowed to write and thats for a reason)?

And furthermore:
> 
ubuntu@ubuntu:~$ sudo fsck -rfv **/dev/sda3**


uhm what ... which ... where ... huh?! where did this partition come from? Did you plug/unplug some usb devices?

---

