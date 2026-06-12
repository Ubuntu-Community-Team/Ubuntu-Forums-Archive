---
title: "Recovering data from WD MBWE II NAS in RAID 1"
date: 2015-12-12
forum: General Help
---

### Post by gilsonsjc on 2015-12-12
Hello everybody, greetings from Brazil

  (You can start reading here or skip all the history and jump all the way to the **"Here is how "newdisk0" looks like"** section)

  I have one WD MBWE II NAS with 2x2TB disks (I will call them "disk0" and "disk1" from now on) which were running on RAID 1. "disk0" failed and need to be replaced. I took the opportunity and made a disk upgrade, got 2x5TB disks (I will call them "newdisk0" and "newdisk1" from now on).

  The NAS has a really crappy system: i tried to install "newdisk0" and "newdisk1" following the steps available by the manufacture and it did not work out so I ended up installing both disks in the NAS as new disks. After that, I tried to use only "disk1" in the NAS so that I could recover the data, unfortunaly the NAS was not able to boot so I ran a program available [here]("http://mybookworld.wikidot.com/mybook-live-debricking-guide-osx-and-windows") (with the option to keep the data) to try to boot it and it did not work.

  I took the "newdisk0" to be my back up disk to be used throughout the data recovering work. So with the help of [tgalati4]("http://ubuntuforums.org/member.php?u=241895") I took images from the "disk0" and "disk1" and save them in "newdisk0" using ddrescue.
  
  ddrescue copied all the data from "disk1" without any error which resulted in a 2 TB image file. The same did not happen with the copy of "disk0": it gave a lot or issues and the image size is 177GB - which shows that might be something really wrong there.


  **Here is how "newdisk0" looks like**
  ```

root@ubuntu:/media/ubuntu/bckp# ls -ln
-rw-r--r-- 1   0   0         79822 Dec 12 08:32 image-disk-0.log
-rw-r--r-- 1   0   0  177946230784 Dec 12 09:06 image-disk-0.raw
-rw-r--r-- 1   0   0           357 Dec 12 18:22 image-disk-1.log
-rw-r--r-- 1   0   0 2000398934016 Dec 12 18:22 image-disk-1.raw

```

  **What I need your help with**:
  1) Recover the partitions from **image-disk-1.raw**
  2) Mount the partition from **image-disk-1.raw** that contains the data I need to recover
  3) Recover the data and get out of your hair! :D

  One detail: I am running the latest Ubuntu version from a USB pen drive and I have 2 available Sata ports to connect the disks. I still have "newdisk1" in case needed, however, since it takes forever to make copies (it took ddrescue 8 hours to build image-disk-1.raw), I would rather work with the images I already have first.

Thanks for your help!
Gilson

---

### Post by gilsonsjc on 2015-12-13
Updates from today
1) I've created a copy of "disk1" using ddrescue to **"newdisk1"**
```
ubuntu@ubuntu:~/Desktop$ sudo ddrescue -d --force /dev/sdb /dev/sda
~/Desktop/copy-disk1-newdisk1.log
GNU ddrescue 1.19
Press Ctrl-C to interrupt
rescued:     2000 GB,  errsize:       0 B,  current rate:   31285 kB/s
     ipos:     2000 GB,   errors:       0,    average rate:   83083 kB/s
    opos:     2000 GB, run time:    6.68 h,  successful read:       0 s ago
Finished
ubuntu@ubuntu:~/Desktop$
```

2) I've written/recovered the lost linux raid partition using testdisk. This is how **"newdisk1"** looks like
```

root@ubuntu:/home/ubuntu# fdisk -l /dev/sda
Disk /dev/sda: 4.6 TiB, 5000981078016 bytes, 9767541168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 434961F3-7564-3148-BF16-D0C0A3318DAF

Device       Start        End    Sectors  Size Type
/dev/sda1  6474176 3907028869 3900554694  1.8T Linux RAID

```

3) I tried to mount /dev/sda1 (recovered linux raid partition) so that I can recover the data. Here is what I've tried to far
```

root@ubuntu:/home/ubuntu# sudo mdadm --assemble --scan
mdadm: failed to add /dev/sda1 to /dev/md2: Invalid argument
mdadm: failed to RUN_ARRAY /dev/md2: Invalid argument
root@ubuntu:/home/ubuntu# mdadm --examine --scan >> /etc/mdadm/mdadm.conf
root@ubuntu:/home/ubuntu# sudo mdadm --assemble --scan
root@ubuntu:/home/ubuntu# mdadm -A -R /dev/md2 /dev/sda1
mdadm: we match both /dev/md2 and /dev/md/2 - cannot decide which to use.
```

This is how the the file **/etc/mdadm/mdadm.conf** looks like:
```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md2  metadata=1.2 UUID=526a8857:b89fdd6c:0006681b:33dc3bf6
name=MyBookWorld:2
ARRAY /dev/md/2  metadata=1.2 UUID=526a8857:b89fdd6c:0006681b:33dc3bf6
name=MyBookWorld:2

```

4) Then I tried to install **newdisk1** directly and alone in the NAS - it did not boot up (I've tried to use both HDD slots in the NAS and the output was the same on either one of them).

5) Then I tried the procedure from this page [http://mybookworld.wikidot.com/mybook-live-debricking-guide-osx-and-windows](http://mybookworld.wikidot.com/mybook-live-debricking-guide-osx-and-windows) (used the command sudo bash ./debrick.sh rootfs.img /dev/sda) on **newdisk1**, here is the output:
```

root@ubuntu:/home/ubuntu/Desktop/Debrick# bash ./debrick.sh rootfs.img /dev/sda

********************** DISK           **********************

script will use the following disk:

Model: ATA WDC WD50EZRX-00M (scsi)
Disk /dev/sda: 5001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      3315MB  2000GB  1997GB                     raid

is this REALLY the disk you want? [y] Y

********************** IMAGE          **********************

swap.c:12:1: warning: return type defaults to ‘int’ [-Wimplicit-int]
 main(int argc, char *argv[])
 ^
swap.c: In function ‘main’:
swap.c:32:9: warning: implicit declaration of function ‘lseek64’
[-Wimplicit-function-declaration]
     if (lseek64(fd, offset, 0) < 0LL) {
         ^

********************** IMPLEMENTATION **********************

everything is now prepared!
device:       /dev/sda
image_img:    rootfs.img
destroy:      false

this is the point of no return, continue? [y] y


mdadm: /dev/sda1 appears to be part of a raid array:
       level=raid1 devices=2 ctime=Sun Dec 13 21:43:01 2015
mdadm: size set to 1950277248K
mdadm: automatically enabling write-intent bitmap on large array
mdadm: creation continuing despite oddities due to --run
mdadm: array /dev/md0 started.
mke2fs 1.42.12 (29-Aug-2014)
Creating filesystem with 487569312 4k blocks and 121896960 inodes
Filesystem UUID: 824198f5-0c97-46ea-9602-0b3e06f41c61
Superblock backups stored on blocks:
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
    102400000, 214990848

Checking for bad blocks (read-only test):   0.00% done, 0:00 elapsed.
(0/0/0 errdone
Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

mdadm: Cannot find /dev/sda2: No such file or directory

synchronize raid... done

copying image to disk...
3999616+0 records in
3999616+0 records out
2047803392 bytes (2.0 GB) copied, 44.0197 s, 46.5 MB/s
mdadm: stopped /dev/md0
lseek64: Success
/dev/sda2: No such file or directory

all done! device should be debricked!

root@ubuntu:/home/ubuntu/Desktop/Debrick#

```
I added "newdisk1" back in NAS - it did not boot up again.

Back again to the computer, I tried to mount it one more time:
```

root@ubuntu:/home/ubuntu# fdisk -l
Disk /dev/sda: 4.6 TiB, 5000981078016 bytes, 9767541168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 434961F3-7564-3148-BF16-D0C0A3318DAF

Device       Start        End    Sectors  Size Type
/dev/sda1  6474176 3907028869 3900554694  1.8T Linux RAID

root@ubuntu:/home/ubuntu# mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : c1e1a4cb:d08df212:e368bf24:bd0fce41 (local to host ubuntu)
  Creation Time : Sun Dec 13 21:44:17 2015
     Raid Level : raid1
  Used Dev Size : 1950277248 (1859.93 GiB 1997.08 GB)
     Array Size : 1950277248 (1859.93 GiB 1997.08 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0

    Update Time : Mon Dec 14 01:35:17 2015
          State : clean
Internal Bitmap : present
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0
       Checksum : fd2e571d - correct
         Events : 37


      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       0        0        1      faulty removed
root@ubuntu:/home/ubuntu# mdadm -A -R /dev/md9 /dev/sda1
mdadm: /dev/md9 has been started with 1 drive (out of 2).
root@ubuntu:/home/ubuntu# 

```

At this moment the drive mounted. However, when I navigate through it I couldn't find my data. I looked at the folder **"DataVolume"** which was empty. I also used the search feature for a folder I know and it did not return any result. 

Also looked at the disk properties and it says only 500MB is used and the 1,4 TB is available, here is the screenshot:
[ATTACH=CONFIG]266140[/ATTACH]

Right now I've got 2 options to work with:
1) The **image-disk-1.raw** copied to **newdisk0**
2) The disk1 copy in **newdisk1** with restored partition

I am stuck, but I feel I am really near to solution this problem and I am sure if your help I will finally be able to recover my data.

---

### Post by gilsonsjc on 2015-12-14
Today I've lost **newdisk0** - it stopped working - I got in touch with WD to replace it.

So now I just have **newdisk1**. 

Here are the things I have tried today:
1) I ran testdisk and was able to recover remaining 3 lost partitions on **newdisk1** that were part of the ones created by NAS (it used to have only **/dev/sdb4**)
```
Disk /dev/sdb: 4.6 TiB, 5000981078016 bytes, 9767541168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 976B5EB1-CD6F-834F-83B3-ABDD43C1C2BE

Device       Start        End    Sectors   Size Type
/dev/sdb1    64320    3984191    3919872   1.9G Linux RAID
/dev/sdb2  3984192    4498111     513920   251M Linux RAID
/dev/sdb3  4498176    6474111    1975936 964.8M Linux RAID
/dev/sdb4  6474176 3907028869 3900554694   1.8T Linux RAID

```

2) Then I tried to plug it in the NAS and it did not boot up.

3) I tried the procedure from this page again [http://mybookworld.wikidot.com/mybook-live-debricking-guide-osx-and-windows]("http://mybookworld.wikidot.com/mybook-live-debricking-guide-osx-and-windows"). This time it did not take a long time to run as before when the disk had only one partition and I had a different output:
```
ubuntu@ubuntu:~/Desktop/debrick$ sudo bash ./debrick.sh rootfs.img /dev/sdb

********************** DISK           **********************

script will use the following disk: 

Model: ATA WDC WD50EZRX-00M (scsi)
Disk /dev/sdb: 5001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      32.9MB  2040MB  2007MB  ext3                  raid
 2      2040MB  2303MB  263MB   linux-swap(v1)        raid
 3      2303MB  3315MB  1012MB  ext3                  raid
 4      3315MB  2000GB  1997GB                        raid

is this REALLY the disk you want? [y] y

********************** IMAGE          **********************

swap.c:12:1: warning: return type defaults to &#8216;int&#8217; [-Wimplicit-int]
 main(int argc, char *argv[])
 ^
swap.c: In function &#8216;main&#8217;:
swap.c:32:9: warning: implicit declaration of function &#8216;lseek64&#8217; [-Wimplicit-function-declaration]
     if (lseek64(fd, offset, 0) < 0LL) {
         ^

********************** IMPLEMENTATION **********************

everything is now prepared!
device:       /dev/sdb
image_img:    rootfs.img
destroy:      false

this is the point of no return, continue? [y] y


mdadm: /dev/sdb1 appears to contain an ext2fs file system
       size=1999808K  mtime=Mon Sep 10 19:29:08 2012
mdadm: size set to 1959872K
mdadm: creation continuing despite oddities due to --run
mdadm: array /dev/md0 started.
mke2fs 1.42.12 (29-Aug-2014)
/dev/md0 contains a ext3 file system
	last mounted on Mon Sep 10 19:29:08 2012
Proceed anyway? (y,n) y
Creating filesystem with 489968 4k blocks and 122640 inodes
Filesystem UUID: d6d13ee4-1f8e-4904-9ead-a7fe334fe1c0
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912

Checking for bad blocks (read-only test):   0.00% done, 0:00 elapsed. (0/0/0 errdone                                                 
Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (8192 blocks): done
Writing superblocks and filesystem accounting information: done 

mdadm: /dev/sdb2 not large enough to join array

synchronize raid... done

copying image to disk... 
dd: writing to &#8216;/dev/md0&#8217;: No space left on device
3919745+0 records in
3919744+0 records out
2006908928 bytes (2.0 GB) copied, 40.0899 s, 50.1 MB/s
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
cp: cannot stat &#8216;/mnt/md0/usr/local/share/bootmd0.scr&#8217;: No such file or directory
./debrick.sh: line 359: /mnt/md0/etc/nas/service_startup/ssh: No such file or directory
umount: /mnt/md0: not mounted
mdadm: stopped /dev/md0

all done! device should be debricked
```

4) Put it back on the NAS and it did not work again.

5) I tried to mount it on the computer again and I am getting only issues
```
root@ubuntu:/home/ubuntu/Desktop/debrick# mdadm --examine /dev/sdb4
/dev/sdb4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 526a8857:b89fdd6c:0006681b:33dc3bf6
           Name : MyBookWorld:2
  Creation Time : Thu Sep 11 03:11:31 2014
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 3900554687 (1859.93 GiB 1997.08 GB)
     Array Size : 1950277343 (1859.93 GiB 1997.08 GB)
  Used Dev Size : 3900554686 (1859.93 GiB 1997.08 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
   Unused Space : before=192 sectors, after=18446744073709551352 sectors
          State : clean
    Device UUID : 90cee8ad:2be82b45:f50ed3da:e7e35200

    Update Time : Fri Nov 27 12:07:42 2015
       Checksum : e1ea4107 - correct
         Events : 1454662


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)

root@ubuntu:/home/ubuntu/Desktop/debrick# mdadm -A -R /dev/md9 /dev/sdb4
mdadm: we match both /dev/md/2 and /dev/md/2 - cannot decide which to use.

root@ubuntu:/home/ubuntu/Desktop/debrick# mdadm --examine --scan >> /etc/mdadm/mdadm.conf

root@ubuntu:/home/ubuntu/Desktop/debrick# mdadm --assemble --scan
mdadm: Devices UUID-fc06eaf0:4d347f68:3b6d8c49:0838e6b9 and UUID-fc06eaf0:4d347f68:3b6d8c49:0838e6b9 have the same name: /dev/md1
mdadm: Duplicate MD device names in conf file were found.

```

This is how the the file** /etc/mdadm/mdadm.conf** looks like:
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md1 UUID=fc06eaf0:4d347f68:3b6d8c49:0838e6b9
ARRAY /dev/md3 UUID=6117e274:fa7501dd:3b6d8c49:0838e6b9
ARRAY /dev/md/2  metadata=1.2 UUID=526a8857:b89fdd6c:0006681b:33dc3bf6 name=MyBookWorld:2

# This file was auto-generated on Mon, 14 Dec 2015 16:34:11 +0000
# by mkconf $Id$
ARRAY /dev/md1 UUID=fc06eaf0:4d347f68:3b6d8c49:0838e6b9
ARRAY /dev/md3 UUID=6117e274:fa7501dd:3b6d8c49:0838e6b9
ARRAY /dev/md/2  metadata=1.2 UUID=526a8857:b89fdd6c:0006681b:33dc3bf6 name=MyBookWorld:2
ARRAY /dev/md1 UUID=fc06eaf0:4d347f68:3b6d8c49:0838e6b9
ARRAY /dev/md3 UUID=6117e274:fa7501dd:3b6d8c49:0838e6b9
ARRAY /dev/md/2  metadata=1.2 UUID=526a8857:b89fdd6c:0006681b:33dc3bf6 name=MyBookWorld:2
```

Guys, I really need some help here! 

Thanks

---

### Post by tgalati4 on 2015-12-15
Well, you certainly have done your homework.  The initial failure from using the "debrick" script is possibly related to not having a big enough swap partition on your disk.  I assume the NAS has limited RAM and uses a  swap partition to extend the RAM.  So, double the size of the swap partition to your newdisk1 and try the debrick script again.  I presume that each original disk had a 263 MB swap to give you a 512 MB swap, which is a common size for an embedded distribution.

If that doesn't work, then use *testdisk* and have it fix the partition to type "ext4" instead of RAID.  You might be able to do this in *parted* as well, but try *testdisk* first.  Once it has the label as ext4, then it might have a chance to be mountable under linux using a SATA connector, not in the NAS enclosure.

---

### Post by gilsonsjc on 2015-12-16
> **tgalati4 said:**
> Well, you certainly have done your homework.  The initial failure from using the "debrick" script is possibly related to not having a big enough swap partition on your disk.  I assume the NAS has limited RAM and uses a  swap partition to extend the RAM.  So, double the size of the swap partition to your newdisk1 and try the debrick script again.  I presume that each original disk had a 263 MB swap to give you a 512 MB swap, which is a common size for an embedded distribution..

Here is how the current partitions look like in **newdisk1**
[ATTACH=CONFIG]266193[/ATTACH]

When I right click and then "Resize/Move" it does not allow me to Resize it:
[ATTACH=CONFIG]266194[/ATTACH]

How do I double the size of the swap?

---

### Post by gilsonsjc on 2015-12-17
anybody please!!!

---

### Post by gilsonsjc on 2015-12-17
Guys, please! I need to return the PC to my friend so if you guys can read this comment [http://ubuntuforums.org/showthread.php?t=2306148&p=13407660#post13407660]("http://ubuntuforums.org/showthread.php?t=2306148&p=13407660#post13407660") I would be really glad!!! 

Thanks!

---

### Post by gilsonsjc on 2015-12-18
> **gilsonsjc said:**
> Here is how the current partitions look like in **newdisk1**
[ATTACH=CONFIG]266193[/ATTACH]

How do I double the size of the swap?

I managed to take 256MB from /dev/sdb1 and "gave it" to /dev/sb2 (swap).

> **tgalati4 said:**
> Well, you certainly have done your homework.  The initial failure from using the "debrick" script is possibly related to not having a big enough swap partition on your disk.  I assume the NAS has limited RAM and uses a  swap partition to extend the RAM.  So, double the size of the swap partition to your newdisk1 and try the debrick script again.  I presume that each original disk had a 263 MB swap to give you a 512 MB swap, which is a common size for an embedded distribution.


I ran the derrick process, mounted the HD in the NAS and it failed to mount. 

> **tgalati4 said:**
> If that doesn't work, then use *testdisk* and have it fix the partition to type "ext4" instead of RAID.  You might be able to do this in *parted* as well, but try *testdisk* first.  Once it has the label as ext4, then it might have a chance to be mountable under linux using a SATA connector, not in the NAS enclosure.

I am going to try this tomorrow morning to see what happens.

Thanks!

---

### Post by gilsonsjc on 2015-12-21
> **tgalati4 said:**
> If that doesn't work, then use *testdisk* and have it fix the partition to type "ext4" instead of RAID.  You might be able to do this in *parted* as well, but try *testdisk* first.  Once it has the label as ext4, then it might have a chance to be mountable under linux using a SATA connector, not in the NAS enclosure.

Ok. so I am trying now to do this. Test disk shows me 4 different linux options to select as the new type. Which one should I use?

[ATTACH=CONFIG]266295[/ATTACH]

---

### Post by tgalati4 on 2016-01-08
You can try Linux LVM, which stands for Logical Volume Manager and see if it is successful in rebuilding the file and directory tables.  LVM is built with Ext4 and should mount on just about any Linux distro.  

Let us know how it turns out.

---

