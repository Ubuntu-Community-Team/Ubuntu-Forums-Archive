---
title: "Problem with mounting ext4 partition"
date: 2014-08-06
forum: General Help
---

### Post by trudzki on 2014-08-06
Hello. I have problem with mounting partition (sda5). 
```
sudo mount /dev/sda1 /mnt/temp
``` gives me the following error: 
wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Next, ```
dmesg |tail 
``` gives me: 
[  162.441522] EXT4-fs error (device sda1): ext4_iget:4059: inode #8: comm mount: bad extra_isize (44593 != 256)
[  162.441806] EXT4-fs (sda1): no journal found
[  287.909808] EXT4-fs error (device sda1): ext4_iget:4059: inode #8: comm mount: bad extra_isize (44593 != 256)
[  287.910118] EXT4-fs (sda1): no journal found
[  293.215857] EXT4-fs error (device sda1): ext4_iget:4059: inode #8: comm mount: bad extra_isize (44593 != 256)
[  293.216128] EXT4-fs (sda1): no journal found
[  329.133763] EXT4-fs error (device sda1): ext4_iget:4059: inode #8: comm mount: bad extra_isize (44593 != 256)
[  329.134074] EXT4-fs (sda1): no journal found
[  392.320184] EXT4-fs error (device sda1): ext4_iget:4059: inode #8: comm mount: bad extra_isize (44593 != 256)
[  392.320610] EXT4-fs (sda1): no journal found

What should do I to correctly mount my partition?

---

### Post by Bashing-om on 2014-08-06
trudzki; Hi !

Right off hand, can not tell ..
You are trying to mount 'sda5' but the system is advising of problems with 'sda1' .
> 
wrong fs type, bad option, bad superblock on /dev/[color=red]sda1[/color],


Getting prepared to run a file system check, show us the outputs of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
[INDENT][INDENT]on the way to find out
[/INDENT][/INDENT]

---

### Post by trudzki on 2014-08-06
sudo fdisk -lu:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004d94d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   348162047   174080000   83  Linux
/dev/sda2       460802048   461006847      102400    7  HPFS/NTFS/exFAT
/dev/sda3       461006848   608462847    73728000    7  HPFS/NTFS/exFAT
/dev/sda4       348164094   460802047    56318977    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       348164096   452716830    52276367+  83  Linux
/dev/sda6       452718592   460802047     4041728   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mmcblk0: 1977 MB, 1977614336 bytes
64 heads, 63 sectors/track, 957 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b2440

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *         135     3858623     1929244+   6  FAT16
```


sudo parted -l:

```
Model: ATA ST320LT020-9YG14 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  178GB  178GB   primary   ext4            boot
 4      178GB   236GB  57.7GB  extended
 5      178GB   232GB  53.5GB  logical   ext4
 6      232GB   236GB  4139MB  logical   linux-swap(v1)
 2      236GB   236GB  105MB   primary   ntfs
 3      236GB   312GB  75.5GB  primary   ntfs


Model: SD SU02G (sd/mmc)
Disk /dev/mmcblk0: 1978MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      69.1kB  1976MB  1976MB  primary  fat16        boot
```

sudo blkid:

```
/dev/sda1: UUID="5d520ff1-c5c4-49ad-9b2d-ea17ad99a19f" TYPE="ext4" 
/dev/sda2: LABEL="System Reserved" UUID="26BE2CE2BE2CABED" TYPE="ntfs" 
/dev/sda3: UUID="2EC8F3E9C8F3ACE9" TYPE="ntfs" 
/dev/sda5: UUID="32c4b88d-7553-4217-ad3f-e706ed2426ab" TYPE="ext4" 
/dev/sda6: UUID="204481cc-abfa-4746-a501-31750663c92e" TYPE="swap" 
/dev/mmcblk0p1: SEC_TYPE="msdos" UUID="3735-3130" TYPE="vfat" 
```


Sory for disorder. Now I have two instances of xUbuntu - one on sda5 and second on sda1. It seems that currently running system is on sda5. And I am not allowed to mount sda1. It was my mistake in previous post - I mentioned sda1, not sda 5. Sorry for this.

---

### Post by coffeecat on 2014-08-06
@trudzki, I've edited your previous post to put the code tags in the right place. The idea of the code tags is to go around terminal output (or other things) to preserve formatting.

---

### Post by Bashing-om on 2014-08-06
trudzki; Well;

'fdisk" sees no problem, so let's proceed to try and mount 'sda1' ( which by-the-way holds the master boot code).
Next step is to look at how we are going to mount 'sda1'.
Anything now present we want to work with ?
Post back - between code tags - the outputs of terminal commands:
```

ls -la /mnt
ls -la /media
ls -la /media/<Your_user_name_Here>

``` so I know there is no conflict of interest in what I have next in mind.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


[INDENT][INDENT]one step at a time 
[INDENT][INDENT][INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by trudzki on 2014-08-06
```
~$ ls -la /mnt
total 20
drwxr-xr-x  5 root root 4096 Aug  6 14:35 .
drwxr-xr-x 23 root root 4096 Aug  6 16:15 ..
drwxr-xr-x 23 root root 4096 Aug  6 16:15 root
drwxr-xr-x 23 root root 4096 Aug  6 16:15 temp
drwxr-xr-x  2 root root 4096 Aug  6 14:34 temp1

```

```

~$ ls -la /media
total 12
drwxr-xr-x   3 root root 4096 Aug  6 14:24 .
drwxr-xr-x  23 root root 4096 Aug  6 16:15 ..
drwxr-x---+  2 root root 4096 Aug  6 15:37 tomek

```

```

~$ ls -la /media/tomek
total 8
drwxr-x---+ 2 root root 4096 Aug  6 15:37 .
drwxr-xr-x  3 root root 4096 Aug  6 14:24 ..


```

It seems that sda1 is not mounted.

---

### Post by Bashing-om on 2014-08-06
trudzki; Hi !

'sda1' would not be mounted unless there is an entry in the 'fstab' file to do so OR you have mounted the partition from the file manager's icon.
OK, one other thing to look at to clear my own mind:
```

ls -la /media/tomek

```
Not that it is a big deal, we will make a new mount point for 'sda1' // but;

[INDENT][INDENT][INDENT]safety is no accident
[/INDENT][/INDENT][/INDENT]

---

### Post by yancek on 2014-08-06
Have you tried mounting by specifying the filesystem type?  Both parted and blkid output show it as ext4.

```
sudo mount -t ext4 /dev/sda1 /mnt/temp
```

If that fails, indicate if you get the same error or if not, what error.

---

### Post by trudzki on 2014-08-30
I was on the trip, so I didnt chance to do something with my computer. 
So, I wrote in console: 
> sudo mount -t ext4 /dev/sda1 /mnt/temp

It generates the following error: 
> mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

