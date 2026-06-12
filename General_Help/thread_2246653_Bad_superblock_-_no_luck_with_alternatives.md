---
title: "Bad superblock - no luck with alternatives"
date: 2014-10-02
forum: General Help
---

### Post by rich68 on 2014-10-02
Hi all

I'm wondering if anyone can please help walk me through this to find out if my hard disk is recoverable. I'm using Lubuntu 14.04 and had a crash which I could not recover from even with the SysReq keys. So I had to use the reset button and now it won't boot or mount. I've removed the hard drive and put it in an enclosure and connected it up to another computer running Mint 17 via USB.

It appears that the superblock is bad but I've tried all the suggested alternate ones and get the same error each time (see below).

```
sudo mount -t ext4 /dev/sdb1 /media
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```
sudo fdisk -l /dev/sdb
```
Note: sector size is 4096 (not 512)
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x3b5d of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 15200 cylinders, total 244190646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001d6d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    60000255   239992832   83  Linux
/dev/sdb2        60002302  1953523711  3279118344    5  Extended
/dev/sdb5   ?   996930704  3216149850   286941996   b7  BSDI fs

```
sudo fsck.ext4 -v /dev/sdb1
```
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```

sudo mke2fs -n /dev/sdb1
```
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
14999552 inodes, 59998208 blocks
2999910 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
1831 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872

```
sudo e2fsck -f -b 32768 /dev/sdb1
```
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>



I also tried to make a backup image on sda6:
```
sudo dd if=/dev/sdb1 of=/data/backup-sdb1.img
```
but I stopped it because it was generating a file of over 165 GB even though the sdb1 partition should only be 30 GB (including unused space).

Is there any hope or does the drive look fried? I'm only really bothered about sdb1 since it contains stuff from the last few weeks on the desktop. Everything else (mainly sdb6 which seems to be missing) is backed up.

Any suggestions appreciated.
Richard

---

