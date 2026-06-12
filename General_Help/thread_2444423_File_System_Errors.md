---
title: "File System Errors"
date: 2020-05-30
forum: General Help
---

### Post by GirishSharma on 2020-05-30
```

(base) girish@gk:~$ sudo fdisk -l
[sudo] password for girish: 
Disk /dev/loop0: 9.7 MiB, 9506816 bytes, 18568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 93.8 MiB, 98336768 bytes, 192064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 111.6 MiB, 116457472 bytes, 227456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 140.68 MiB, 147501056 bytes, 288088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 156.7 MiB, 164290560 bytes, 320880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 255.58 MiB, 267980800 bytes, 523400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 200 KiB, 204800 bytes, 400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 154.26 MiB, 161751040 bytes, 315920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM010-2EP1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x2052474d

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1          6579571 1924427647 1917848077 914.5G 70 DiskSecure Multi-Boot
/dev/sdb2       1953251627 3771827541 1818575915 867.2G 43 unknown
/dev/sdb3        225735265  225735274         10     5K 72 unknown
/dev/sdb4       2642411520 2642463409      51890  25.3M  0 Empty

Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.
Partition table entries are not in disk order.


Disk /dev/sda: 223.58 GiB, 240057409536 bytes, 468862128 sectors
Disk model: WDC WDS240G1G0A-
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5475bcda

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 435589119 435587072 207.7G 83 Linux
/dev/sda2       435591166 468860927  33269762  15.9G  5 Extended
/dev/sda5       435591168 468860927  33269760  15.9G 82 Linux swap / Solaris




Disk /dev/loop8: 160.16 MiB, 167931904 bytes, 327992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 115.16 MiB, 120750080 bytes, 235840 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 10.49 MiB, 10989568 bytes, 21464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 156.19 MiB, 163774464 bytes, 319872 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 140.68 MiB, 147501056 bytes, 288088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 81.52 MiB, 85467136 bytes, 166928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 54.97 MiB, 57614336 bytes, 112528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 67.29 MiB, 70549504 bytes, 137792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 128 KiB, 131072 bytes, 256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 2.68 MiB, 2797568 bytes, 5464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 54.97 MiB, 57618432 bytes, 112536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop19: 9.7 MiB, 9510912 bytes, 18576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop20: 3.7 MiB, 3862528 bytes, 7544 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop21: 48.3 MiB, 50642944 bytes, 98912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop22: 93.94 MiB, 98484224 bytes, 192352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop23: 81.52 MiB, 85463040 bytes, 166920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop24: 62.9 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop25: 2.17 MiB, 2273280 bytes, 4440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

(base) girish@gk:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal

(base) girish@gk:~$ uname -a
Linux gk 5.4.0-33-generic #37-Ubuntu SMP Thu May 21 12:53:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
(base) girish@gk:~$ 

```

As you can see above, there are some errors is showing and one of partition i.e. /dev/sdb2 is saying "Structure need Cleaning".  After Google, I could not find any solution, so I am writing here.  This is my home learning PC. Kindly help me to -

1.Remove Structure need Cleaning error from /dev/sdb2
2.Above "Partition <N> does not start on physical sector boundary." error messages.

Update :

```

root@gk:/home/girish# fsck /dev/sdb
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Found a atari partition table in /dev/sdb
root@gk:/home/girish# 

Output of fsck -y /dev/sdb2 


Group descriptor 2768 checksum is 0x9d7e, should be 0x24cc.  FIXED.
Block bitmap for group 2769 is not in group.  (block 1593048024)
Relocate? yes

Inode bitmap for group 2769 is not in group.  (block 3295931755)
Relocate? yes

Inode table for group 2769 is not in group.  (block 1565651015)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Group descriptor 2769 checksum is 0x5b27, should be 0xd572.  FIXED.
fsck.ext4: A block group is missing an inode table while reading bad blocks inode
This doesn't bode well, but we'll try to go on...
Pass 1: Checking inodes, blocks, and sizes
Group 497's inode table at 80614994 conflicts with some other fs block.
Relocate? yes

Group 1208's inode table at 167 conflicts with some other fs block.
Relocate? yes

e2fsck: aborted

/dev/sdb2: ***** FILE SYSTEM WAS MODIFIED *****
root@gk:/home/girish# 


```

---

### Post by dino99 on 2020-05-30
Read that howto to solve your sdb2/3 issues  [https://linuxconfig.org/how-to-force-fsck-to-check-filesystem-after-system-reboot-on-linux](https://linuxconfig.org/how-to-force-fsck-to-check-filesystem-after-system-reboot-on-linux)

---

### Post by GirishSharma on 2020-05-30
Sorry, but not useful. Still I am getting "Structure need cleaning" issue on /dev/sdb2.

---

### Post by GirishSharma on 2020-05-30
Any update please !

---

### Post by TheFu on 2020-05-30
[LIST]
[*]a) Since 16.04 the sudo touch /forcefsck trick doesn't work.
[*]b) Running fsck can only be done on partitions or LVs with file systems, NEVER EVER the entire drive.  sdb is a drive. sdb1 is the first partition on the drive.  sdb2 is the second partition.
[*]c) fsck cannot be run on "active partitions" - basically the file system cannot be mounted.  That often leads to a chicken-egg problem.
[*]d) The solution to the "chicken-egg" problem is to go into the "Advanced" boot menu, enter the Ubuntu Recovery Mode, then find the choice for "fsck all" and select that.
[*]e) An alternative to using the Advanced boot menu is to boot from an Ubuntu Install flash drive and go into "Try Ubuntu" mode.  Then find the disks and partition using whatever commands you like ... I prefer using **lsblk** and **sudo parted -lm** to get to the point.  Then run **sudo fsck /dev/sd[a-z][1-99] }** each in turn.  Don't run it against the swap partition, if there is one. Looks like "5" is the swap. The device names can change from boot -to- boot, so with every reboot, we have to check them again if we use /dev/sd-whatever.
[/LIST]

This is all basic Linux admin skills.  How to do this stuff is in any beginner Linux Admin book and probably in the "Ubuntu Desktop Guide" and the "Ubuntu Server Guide."  Google finds them easily.
A Linux book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Chapter 15.

There are other ways to get fsck to run, but those are usually more painful.

Only run fsck on non-active, file systems, nothing else.

---

### Post by GirishSharma on 2020-05-31
> **TheFu said:**
> 
[LIST]
[*]a) Since 16.04 the sudo touch /forcefsck trick doesn't work. 
[*]b) Running fsck can only be done on partitions or LVs with file systems, NEVER EVER the entire drive.  sdb is a drive. sdb1 is the first partition on the drive.  sdb2 is the second partition. 
[*]c) fsck cannot be run on "active partitions" - basically the file system cannot be mounted.  That often leads to a chicken-egg problem. 
[*]d) The solution to the "chicken-egg" problem is to go into the "Advanced" boot menu, enter the Ubuntu Recovery Mode, then find the choice for "fsck all" and select that. 
[*]e) An alternative to using the Advanced boot menu is to boot from an Ubuntu Install flash drive and go into "Try Ubuntu" mode.  Then find the disks and partition using whatever commands you like ... I prefer using **lsblk** and **sudo parted -lm** to get to the point.  Then run **sudo fsck /dev/sd[a-z][1-99] }** each in turn.  Don't run it against the swap partition, if there is one. Looks like "5" is the swap. The device names can change from boot -to- boot, so with every reboot, we have to check them again if we use /dev/sd-whatever. 
[/LIST]

This is all basic Linux admin skills.  How to do this stuff is in any beginner Linux Admin book and probably in the "Ubuntu Desktop Guide" and the "Ubuntu Server Guide."  Google finds them easily.
A Linux book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Chapter 15.

There are other ways to get fsck to run, but those are usually more painful.

Only run fsck on non-active, file systems, nothing else.

Thanks for your reply and I am sorry for late response. Whatever you suggested i.e. to run fsck in recovery mode on Partitions, I could not succeed. Then after many efforts, I did this :

```

(base) girish@gk:~/e2fsprogs-1.43.1/e2fsck$ sudo ./e2fsck /dev/sdb2


Clear? yes

Extended attribute block for inode 2006307 (...) is invalid (3022510107).
Clear? yes

Unattached inode 2006307
Connect to /lost+found? yes

Inode 2006307 ref count is 63572, should be 1.  Fix? yes

i_faddr for inode 2006308 (...) is 1320338271, should be zero.
Clear? yes

i_file_acl_hi for inode 2006308 (...) is 34270, should be zero.
Clear? yes

Extended attribute block for inode 2006308 (...) is invalid (3639776645).
Clear? yes

Unattached inode 2006308
Connect to /lost+found? yes

No room in lost+found directory.  Expand? yes

Signal (11) SIGSEGV si_code=SEGV_MAPERR fault addr=(nil)
./e2fsck(+0x37b39)[0x55b24bf4db39]
/lib/x86_64-linux-gnu/libpthread.so.0(+0x153c0)[0x7f5f47e863c0]
/lib/x86_64-linux-gnu/libc.so.6(+0x18e6f5)[0x7f5f47e0d6f5]
./e2fsck(+0x62185)[0x55b24bf78185]
./e2fsck(ext2fs_zero_blocks2+0x85)[0x55b24bf6bdc5]
./e2fsck(+0x29ac7)[0x55b24bf3fac7]
./e2fsck(+0x42e83)[0x55b24bf58e83]
./e2fsck(+0x4399c)[0x55b24bf5999c]
./e2fsck(e2fsck_expand_directory+0xd2)[0x55b24bf40492]
./e2fsck(e2fsck_reconnect_file+0x1d5)[0x55b24bf40715]
./e2fsck(e2fsck_pass4+0x71a)[0x55b24bf416da]
./e2fsck(e2fsck_run+0x5a)[0x55b24bf31b8a]
./e2fsck(main+0xda2)[0x55b24bf2da62]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0x7f5f47ca60b3]
./e2fsck(_start+0x2a)[0x55b24bf2fd7a]
(base) girish@gk:~/e2fsprogs-1.43.1/e2fsck$ 

```

Outcome of above step, it cleared all the data from /dev/sdb2 and it opened the partition but now I am getting the same error with /dev/sdb1 in this style : (I am not able to open the folder in file browser, so I went to terminal)
```

(base) girish@gk:~$ cd /media/drive1
(base) girish@gk:/media/drive1$ ls
ls: cannot access 'glassfish-4.1.1': Structure needs cleaning
ls: cannot access 'netbeans-8.2': Structure needs cleaning
ls: cannot access 'yu yureka': Structure needs cleaning
ls: cannot access 'Refactored_Py_DS_ML_Bootcamp-master': Structure needs cleaning
total 79G
d?????????     ? ?      ?         ?            ? 'yu yureka'
d?????????     ? ?      ?         ?            ?  Refactored_Py_DS_ML_Bootcamp-master
d?????????     ? ?      ?         ?            ?  netbeans-8.2
d?????????     ? ?      ?         ?            ?  glassfish-4.1.1
drwxrwxr-x     2 girish girish 4.0K Dec  7  2016  dtz
drwx------ 16342 root   root   600K Nov  5  2017  lost+found
list of my good files and directories

```

/media/drive1 is /dev/sdb1 which is mounted through fstab which I added.

Now I am struggling for above ???? marked folder. I don't know why life is so tough and getting disappointed.

---

### Post by yancek on 2020-06-01
Your sdb drive seems to be a mess.  I"m not sure what happened there but your initial post shows multiple partitions with filesystem unknown.  Not a good thing.  Your last post seems to indicate that you are now able to access the formerly problematic sdb2 so have you run the same commands on sdb1?  Make sure the partition is not mounted when doing this.

---

### Post by TheFu on 2020-06-01
Just to be clear.

If the file system isn't a native Linux one, don't attempt fsck.  Use Windows tools to fix Windows file systems.  Use Linux tools to fix Linux file systems.  DO NOT ATTEMPT to use fsck on any NTFS or FAT32 or FAT16 or vfat or exfat file system.

Always have backups for anything you are not willing to lose.  Always.

RAID is not a backup. Not ever.

---

