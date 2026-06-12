---
title: "Help with bad superblock on USB flash drive"
date: 2014-04-23
forum: General Help
---

### Post by tstack77 on 2014-04-23
My server fell victim to a power outage while I was out of town, and unfortunately I have been putting off getting nut to work with my off-brand UPS so it didn't shutdown properly . When I restarted I saw this error during post:

EXT4-fs (SDD2): unable to read superblock

SDD is a 16gb usb drive where ubuntu is installed, so not wanting to format the drive I booted up Parted Magic. Below are the outputs of some commands I've read in other threads. I am not sure what to try next and I really appreciate a point in any direction. 

Thanks.

```
root@SERVER:~# fsck.ext4 -v /dev/sdd2
e2fsck 1.42.9 (28-Dec-2013)
/sbin/e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdd2
Could this be a zero-length partition?

root@SERVER:~# sudo mke2fs -n /dev/sdd2
mke2fs 1.42.9 (28-Dec-2013)
mke2fs: inode_size (128) * inodes_count (0) too big for a
        filesystem with 0 blocks, specify higher inode_ratio (-i)
        or lower inode count (-N).

root@SERVER:~# mount -t ext4 /dev/sdd2 /
mount: wrong fs type, bad option, bad superblock on /dev/sdd2,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

root@SERVER:~# dmesg | tail
[   13.617239] Bluetooth: BNEP filters: protocol multicast
[   13.617247] Bluetooth: BNEP socket layer initialized
[   16.076778] NET: Registered protocol family 10
[   16.077054] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.397459] r8169 0000:03:00.0 eth0: link up
[   16.397470] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.263749] Bluetooth: RFCOMM TTY layer initialized
[   28.263763] Bluetooth: RFCOMM socket layer initialized
[   28.263770] Bluetooth: RFCOMM ver 1.11
[  851.995406] EXT4-fs (sdd2): unable to read superblock

root@SERVER:~# smartctl -a /dev/sdd
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.4-pmagic64] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

/dev/sdd: Unknown USB bridge [0x0781:0x5580 (0x010)]
Please specify device type with the -d option.

Use smartctl -h to get a usage summary

root@SERVER:~# fdisk -lu
Disk /dev/sdd: 16.0 GB, 16013942784 bytes, 31277232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk label type: dos
Disk identifier: 0x000a5681

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048      499711      248832   83  Linux
/dev/sdd2          501758    31277055    15387649    5  Extended
/dev/sdd5          501760    31277055    15387648   8e  Linux LVM 
```

---

### Post by Bashing-om on 2014-04-23
tstack77; Hi !

See if slickymaster has you covered !
[http://ubuntuforums.org/showthread.php?t=2177756](http://ubuntuforums.org/showthread.php?t=2177756)

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by tstack77 on 2014-04-23
Thanks for the link. Unfortunately I attempted his method but ran afoul with when trying "sudo mke2fs -n /dev/sdd2". Instead of giving me an output of stored superblocks I got the below output about inodes.

```
root@SERVER:~# sudo mke2fs -n /dev/sdd2
mke2fs: inode_size (128) * inodes_count (0) too big for a
        filesystem with 0 blocks, specify higher inode_ratio (-i)
        or lower inode count (-N)
```

I attempted to find ANY superblocks on SDD and have a strange output that the device is "apparently in use by the system"...apparently? The disk is 100% NOT mounted and I'm running Parted Magic???

```
root@SERVER:~# mke2fs -n /dev/sdd
mke2fs 1.42.9 (28-Dec-2013)
/dev/sdd is entire device, not just one partition!
Proceed anyway? (y,n) y
/dev/sdd is apparently in use by the system; will not make a filesystem here!
```

I'm at a complete loss getting different results from any of the google searches I have made. I'm thinking of pulling the USB stick out of the server and putting it into my desktop to attempt a fix, bad idea?

---

### Post by Bashing-om on 2014-04-23
tstack77; UnGood .

If the file system were in some order, this is what should have resulted:
```

sysop1@u1204:~$ sudo mke2fs -n /dev/sdc1
[sudo] password for sysop1: 
mke2fs 1.42 (29-Nov-2011)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
3203072 inodes, 12800000 blocks
640000 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
391 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424

sysop1@u1204:~$

```(where in this instance is an empty partition)

Might I now suggest to see what the utility testdisk can see ?
```

apt-cache show testdisk
##If you like what you see
##Install ##
sudo apt-get install testdisk

```
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

[INDENT]not much consolation, but
[INDENT][INDENT][INDENT]maybe a bit more help
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tstack77 on 2014-04-23
Here is the cursory output before I search

```
root@SERVER:~# testdisk

Disk /dev/sdd - 16 GB / 14 GiB - CHS 15272 64 32
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    1   0  1   243  63 32     497664

Warning: Bad starting sector (CHS and LBA don't match)
 2 E extended               244  63 31 15271  63 32   30775298

Warning: Bad ending sector (CHS and LBA don't match)
 5 L Linux LVM              245   0  1 15271  63 32   30775296

Warning: Bad ending sector (CHS and LBA don't match)

```

EDIT:
This can't be a good sign. I can't find any documentation to save hese partitions or move forward. The next option is to either 'quit' or 'write'. Is writing going to simply overwrite the bad sectors leaving the majority intact?

```
Disk /dev/sdd - 16 GB / 14 GiB - CHS 15272 64 32

The harddisk (16 GB / 14 GiB) seems too small! (< 20 GB / 19 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  Linux                 6523   0  1 19814  63 32   27222016
   Linux                 6549   1  1 19841   0 32   27222016
   Linux                 6556   0  1 19847  63 32   27222016
   Linux                 6560   1  1 19852   0 32   27222016
   Linux                 6578   1  1 19870   0 32   27222016
   Linux                 6586   1  1 19878   0 32   27222016
   Linux                 6602   0  1 19893  63 32   27222016
   Linux                 6610   0  1 19901  63 32   27222016
   Linux                 6612   2  1 19904   1 32   27222016
   Linux                 6635   2  1 19927   1 32   27222016

[ Continue ]
ext4 blocksize=4096 Large file Sparse superblock Recover, 13 GB / 12 GiB
```

EDIT2:
The testdisk documentation explains that it cannot recovery ext3/ext4 partitions and to try photorec instead. Have ~20mintes left on the photorec scan.

EDIT3:
photorec didn't recover the sectors. I ended up biting the bullet, low-level formatting the drive and starting over; bright side is that I'm now up to date with tahr :-)

THANK YOU again for the help!

---

