---
title: "Lost partition - help me recover my data"
date: 2013-12-02
forum: General Help
---

### Post by Lockheed on 2013-12-02
I'm in trouble. I am trying to recover my main data partition. 

Here's how it happened:

sdb1 - 680gb primary partition, ext4, around 300gb of data on it
sdb2 - 60gb primary partition, ext4, for backing up system from sda1 with rsync

While doing rsync backup on sdb2, I run gparted, which indicated that it cannot read partition table on sdb and displayed the whole of it as unallocated. I know that when I run gparted 30 earlier, the partition was still vissible.
Nevertheless, I thought that's because of rsync and I thought reboot would fix that, because sdb1 was still mounted, and I was accessing all the data on it with no issues.

When rsync was done, I rebooted an that was the last time I saw my data.

Automounting during boot gives me:
```
superblock could not be read or does not describe correct ext2 filesystem...
```

So I tried to run 

```
$ sudo fsck.ext4 -p -b 98304 -B 4096 /dev/sdb
fsck.ext4: Bad magic number in super-block while trying to open /dev/sdb
/dev/sdb: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

```
$ sudo e2fsck -b 8193 /dev/sdb
[sudo] password for juha: 
e2fsck 1.42.8 (20-Jun-2013)
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```
I tried the same command with all superblock backups that were listed.


I then went into testdisk and as I saw it detected sdb1 and sdb2 correctly, I selected "Write" on the partition table. Since then on, gparted sees both partitions, but it sees sdb1 as empty.

I then did this:

```
$ sudo fsck -n /dev/sdb1
fsck from util-linux 2.24
e2fsck 1.42.8 (20-Jun-2013)
ext2fs_check_desc: Corrupt group descriptor: bad block for block bitmap
fsck.ext4: Group descriptors look bad... trying backup blocks...
fsck.ext4: Bad magic number in super-block while using the backup blocksfsck.ext4: going back to original superblock
Superblock has an invalid journal (inode 8).
Clear? no

fsck.ext4: Illegal inode number while checking ext3 journal for /dev/sdb1

/dev/sdb1: ********** WARNING: Filesystem still has errors **********
```

I also run testdisk to see if it can find data from sdb1.
It finds the partition (partition type is automatically selected as None) but it finds no files on sdb1, even after deep search. 
It does find data on sdb2, but that's just system partition backup I don't care about at this point.

Also, just now I run this
```
]$ sudo fsck.ext4 -v /dev/sdb1
e2fsck 1.42.8 (20-Jun-2013)
ext2fs_check_desc: Corrupt group descriptor: bad block for block bitmap
fsck.ext4: Group descriptors look bad... trying backup blocks...
fsck.ext4: Bad magic number in super-block while using the backup blocksfsck.ext4: going back to original superblock
Superblock has an invalid journal (inode 8).
Clear<y>? yes
*** ext3 journal has been deleted - filesystem is now ext2 only ***

Note: if several inode or block bitmap blocks or part
of the inode table require relocation, you may wish to try
running e2fsck with the '-b 32768' option first.  The problem
may lie only with the primary block group descriptors, and
the backup block group descriptors may be OK.

Block bitmap for group 256 is not in group.  (block 1268396107)
Relocate<y>? yes
Inode bitmap for group 256 is not in group.  (block 1125246092)
Relocate<y>? yes
Inode table for group 256 is not in group.  (block 2088878841)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
One or more block group descriptor checksums are invalid.  Fix<y>? yes
Group descriptor 256 checksum is 0x6349, should be 0x9abd.  FIXED.
Inode bitmap for group 257 is not in group.  (block 2837529440)
Relocate<y>? yes
Inode table for group 257 is not in group.  (block 2199953455)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 257 checksum is 0x02d4, should be 0xd13d.  FIXED.
Block bitmap for group 258 is not in group.  (block 3896597355)
Relocate<y>? yes
Inode bitmap for group 258 is not in group.  (block 2097244160)
Relocate<y>? yes
Inode table for group 258 is not in group.  (block 2609271215)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 258 checksum is 0xee91, should be 0xc246.  FIXED.
Block bitmap for group 259 is not in group.  (block 805546298)
Relocate<y>? yes
Inode bitmap for group 259 is not in group.  (block 3538423854)
Relocate<y>? yes
Inode table for group 259 is not in group.  (block 2924444292)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 259 checksum is 0xc190, should be 0x4c0d.  FIXED.
Block bitmap for group 260 is not in group.  (block 338739984)
Relocate<y>? yes
Inode bitmap for group 260 is not in group.  (block 902864749)
Relocate<y>? yes
Inode table for group 260 is not in group.  (block 1901539298)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 260 checksum is 0xac76, should be 0xac63.  FIXED.
Block bitmap for group 261 is not in group.  (block 1660969779)
Relocate<y>? yes
Inode bitmap for group 261 is not in group.  (block 209743725)
Relocate<y>? yes
Inode table for group 261 is not in group.  (block 879935846)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 261 checksum is 0x800e, should be 0x8fa5.  FIXED.
Block bitmap for group 262 is not in group.  (block 1705519300)
Relocate<y>? yes
Inode bitmap for group 262 is not in group.  (block 1360743755)
Relocate<y>? yes
Inode table for group 262 is not in group.  (block 4107065764)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 262 checksum is 0xc00d, should be 0xe8f3.  FIXED.
Inode bitmap for group 263 is not in group.  (block 2205583287)
Relocate<y>? yes
Inode table for group 263 is not in group.  (block 3636737468)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? yes
Group descriptor 263 checksum is 0x69a9, should be 0xb9a9.  FIXED.
Block bitmap for group 264 is not in group.  (block 1471470759)
Relocate<y>? yes
Inode bitmap for group 264 is not in group.  (block 1725839977)
Relocate<y>? yes
Inode table for group 264 is not in group.  (block 2144458553)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 264 checksum is 0xcd09, should be 0xea3a.  FIXED.
Block bitmap for group 265 is not in group.  (block 3617231787)
Relocate<y>? yes
Inode bitmap for group 265 is not in group.  (block 2640198439)
Relocate<y>? yes
Inode table for group 265 is not in group.  (block 2725347176)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 265 checksum is 0xbbb8, should be 0xb870.  FIXED.
Block bitmap for group 266 is not in group.  (block 1840499818)
Relocate<y>? yes
Inode bitmap for group 266 is not in group.  (block 3698703324)
Relocate<y>? yes
Inode table for group 266 is not in group.  (block 2882301371)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 266 checksum is 0xb3c9, should be 0x72d5.  FIXED.
Block bitmap for group 267 is not in group.  (block 1968099309)
Relocate<y>? yes
Inode bitmap for group 267 is not in group.  (block 2125019324)
Relocate<y>? yes
Inode table for group 267 is not in group.  (block 2616321653)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 267 checksum is 0x72bb, should be 0xc66c.  FIXED.
Block bitmap for group 268 is not in group.  (block 3197564106)
Relocate<y>? yes
Inode bitmap for group 268 is not in group.  (block 1173679527)
Relocate<y>? yes
Inode table for group 268 is not in group.  (block 3081059840)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 268 checksum is 0xee4e, should be 0x6c67.  FIXED.
Block bitmap for group 269 is not in group.  (block 467880860)
Relocate<y>? yes
Inode bitmap for group 269 is not in group.  (block 3461842583)
Relocate<y>? yes
Inode table for group 269 is not in group.  (block 903401461)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 269 checksum is 0x701d, should be 0x1735.  FIXED.
Block bitmap for group 270 is not in group.  (block 1737084563)
Relocate<y>? yes
Inode bitmap for group 270 is not in group.  (block 1617385180)
Relocate<y>? yes
Inode table for group 270 is not in group.  (block 3944519733)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 270 checksum is 0x1c78, should be 0x9f4e.  FIXED.
Block bitmap for group 271 is not in group.  (block 3558332121)
Relocate<y>? yes
Inode bitmap for group 271 is not in group.  (block 1481837154)
Relocate<y>? yes
Inode table for group 271 is not in group.  (block 1108213120)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 271 checksum is 0x3066, should be 0xce01.  FIXED.
Block bitmap for group 272 is not in group.  (block 3294840462)
Relocate<y>? yes
Inode bitmap for group 272 is not in group.  (block 1680662834)
Relocate<y>? yes
Inode table for group 272 is not in group.  (block 747037043)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? no
Group descriptor 272 checksum is 0x7d96, should be 0xde7a.  FIXED.
Block bitmap for group 273 is not in group.  (block 805709209)
Relocate<y>? cancelled!
Inode bitmap for group 273 is not in group.  (block 220354588)
Relocate<y>? cancelled!
Inode table for group 273 is not in group.  (block 281430039)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? cancelled!
Group descriptor 273 checksum is 0xa378, should be 0x6f41.  FIXED.

/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****

/dev/sdb1: ********** WARNING: Filesystem still has errors **********
```
But as you can see, I chickened out on "SEVERE DATA LOSS POSSIBLE" warnings, and after few repeats, I just hit ctrl+c not sure if I should even touch that.

And some other commands I tried:
```
$ sudo parted /dev/sdb p
[sudo] password for juha: 
Model: ATA Hitachi HTS54757 (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  684GB  684GB   primary  ext4         boot
 2      684GB   750GB  66.0GB  primary  ext4
```

```
$ sudo dumpe2fs /dev/sdb1 | grep superblock
dumpe2fs 1.42.8 (20-Jun-2013)
dumpe2fs: Invalid argument while reading journal super block
```


```
# sudo mount /dev/loop1 -t ext4 -o ro,offset=32256  /home/juha/diskimage/
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```
I also tried mounting it without help of partition table (not sure if I should use /dev/sdb or /dev/sdb1, so I tried both):
```
$ sudo mount -t ext4 -o ro,offset=32256 /dev/sdb /mnt/Disk_D
mount: wrong fs type, bad option, bad superblock on /dev/loop0,1 /home/juha/diski
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```
```
$ dmesg | tail
[  873.975814] loop: module loaded
[  902.247136] CE: hpet increased min_delta_ns to 20113 nsec
[ 1090.928745] EXT4-fs (loop1): VFS: Can't find ext4 filesystem
[ 1224.940931] EXT4-fs (loop0): VFS: Can't find ext4 filesystem
[  477.255509] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem
```


Here is some output from testdisk while doing deepsearch on partition:

```
  Disk /dev/sdb - 750 GB / 698 GiB - CHS 91201 255 63

     Partition                  Start        End    Size in sectors

   P ext4                     0  32 33 83175 145 42 1336213504
   P ext4                 83175 145 43 91201  52 51  128931840

Write isn't available because the partition table type "None" has been selected.

```
```

ext4                     0  32 33 83175 145 42 1336213504
  ext4                     0  32 31 83175 145 40 1336213504
  ext4                     0  32 33 83175 145 42 1336213504
Warning: number of heads/cylinder mismatches 64 (FAT) != 255 (HD)
Warning: number of sectors per track mismatches 32 (FAT) != 63 (HD)
  FAT12                   20  89  2    20 206 12       7382 [GParted-EFI]
  ext4                     0  32 31 83175 145 40 1336213504
  ext4                     0  32 33 83175 145 42 1336213504
  ext4                     0  32 31 83175 145 40 1336213504
  ext4                     0  32 33 83175 145 42 1336213504
  ext4                     0  32 31 83175 145 40 1336213504
  ext4                     0  32 33 83175 145 42 1336213504
  ext4                     0  32 31 83175 145 40 1336213504
  ext4                     0  32 33 83175 145 42 1336213504
```
```
kpartx -lv /dev/sdb
sdb1 : 0 1336213504 /dev/sdb 2048
sdb2 : 0 128931840 /dev/sdb 1336215552
```

I also run photorec just to have a look, and it seems to be finding all the files, but of course photorec recovery is a massive mess so I would only like to use it as a last resort.

I would really appreciate some help here. 

I had online backup of ~10 GB of the most important data of it, but there still is on this lost partition at least another 10-20 GB of really vital data, the loss of which would be quite a blow.

---

### Post by oldfred on 2013-12-02
You tried running most of your fsck or e2fsck on sdb, you can only run it on the partitions sdb1 or sdb2, so most of the errors you are getting are because you are running against a drive which does not have any data.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Try again on sdb2


And if trying backup superblocks it must be a partition.

---

### Post by Lockheed on 2013-12-02
This disk is separate from my system disk, so I think there is no need to run LiveCD.

I am afraid of running e2fsck on it because I have been warned that
> fsck is always a last ditch thing to try. It may make the filesystem metadata self consistent but it can trash your data in the process.
and e2fsck does the same thing, doesn't it?

---

### Post by oldfred on 2013-12-02
I think fsck now calls e2fsck, but you have run it with slighty different parameters already based on your post above.

---

### Post by Lockheed on 2013-12-02
.> e2fsck -C0 -p -f -v /dev/sdb1
[sudo] password for juha: 
/dev/sdb1: Note: if several inode or block bitmap blocks or part
of the inode table require relocation, you may wish to try
running e2fsck with the '-b 32768' option first.  The problem
may lie only with the primary block group descriptors, and
the backup block group descriptors may be OK.

/dev/sdb1: Block bitmap for group 256 is not in group.  (block 1268396107)


/dev/sdb1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)

---

### Post by oldfred on 2013-12-02
Then try this:
sudo e2fsck -f -y -v /dev/sdb1

Then all you can do is the alternative superblocks.

Does drive show ok in Disks or Disk Utility and Smart Status. All I know is passed is good and anything else is an issue.

---

### Post by theantibob on 2013-12-02
> **Lockheed said:**
> Write isn't available because the partition table type "None" has been selected.

Perhaps the partition table type is the problem? Shouldn't it be DOS or something along those lines? I forget. You shouldn't work directly with disks when trying to recover data (although i have successfully, due to available storage space issues), you should make an image to work with.

But one thing is for sure, if you need some help recovering data, [THIS]("http://forum.cgsecurity.org/phpBB3/") is the place to ask questions or find information.

---

### Post by oldfred on 2013-12-02
I missed the none. It looks like it should be the Intel choice for standard MBR(msdos) partitioning.

screens shown here.
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Lockheed on 2013-12-03
Finally, I bit the bullet and I run ```
fsck -b 32768 /dev/sdb1 -y -C0
``` After 2 hours of fixing inodes and other things, it was done. It ended up saying that partition still contain errors, but I was able to mount it no normal way.

Data size went from 330GB to 190GB and all of it was in lost+found, out of which I copied off the disk ~80GB. The rest was a numerical mess.

So I now gonna restore the image backup back on the disk and go back to square one trying to retrieve at least part of the rest. 

I look forward to your advices.

---

### Post by oldfred on 2013-12-03
Did you use testdisk with Intel setting for MBR(msdos) partitioning?

---

### Post by Lockheed on 2013-12-03
Yes, it makes no difference. Both modes detect partition and both show no files on it

---

### Post by oldfred on 2013-12-03
Then photorec or similar tools that just scan drive for anything that looks like a file may be the only choice. 
I have used it. It is slow as it has to scan entire drive. It also finds deleted files or parts of some delete files. I had saved some text files many times and it found all the old copies. I had to manually sort thru to figure out which was newer and never knew for sure. You do not recover full file names, just extensions. But photo have meta-data that you can use to restore a date.

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)

---

