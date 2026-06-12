---
title: "fsck runs out of memory when trying to fix a LVM partition on 1 TB drive."
date: 2013-03-16
forum: General Help
---

### Post by PatrickD-52761 on 2013-03-16
Hello everyone,

What I have is this: I've got Lubuntu installed on the first partition of my 1TB drive (taking up 500GB roughly) and Fedora 18 installed on the other 500GB (using a LVM setup).  When I try mounting the LVM in Lubuntu, so I can update GRUB, I get this error:

```

mount: wrong fs type, bad option, bad superblock on /dev/mapper/fedora_dcky--fedora--test-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



```

And dmesg | tail shows

```

$dmesg | tail
[333729.657689] JFS: nTxBlock = 8192, nTxLock = 65536
[333729.718391] NTFS driver 2.1.30 [Flags: R/O MODULE].
[333729.758285] QNX4 filesystem 0.2.3 registered.
[333729.869467] Btrfs loaded
[333839.816217] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[333840.383616] EXT4-fs (dm-2): ext4_check_descriptors: Checksum for group 0 failed (6072!=0)
[333840.383623] EXT4-fs (dm-2): group descriptors corrupted!
[337142.256748] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[337142.659237] EXT4-fs (dm-2): ext4_check_descriptors: Checksum for group 0 failed (6072!=0)
[337142.659243] EXT4-fs (dm-2): group descriptors corrupted!



```

I've tried running fsck -y on the partition, and it runs out of memory before it's finished.

```

sudo fsck -y /dev/mapper/fedora_dcky--fedora--test-root
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
ext2fs_check_desc: Corrupt group descriptor: bad block for block bitmap
fsck.ext4: Group descriptors look bad... trying backup blocks...
/dev/mapper/fedora_dcky--fedora--test-root contains a file system with errors, check forced.
Resize inode not valid.  Recreate? yes


Pass 1: Checking inodes, blocks, and sizes
Inode 2027008 has illegal block(s).  Clear? yes


Illegal block #2 (213909536) in inode 2027008.  CLEARED.
Illegal block #5 (226492416) in inode 2027008.  CLEARED.
Illegal block #8 (268435456) in inode 2027008.  CLEARED.
Illegal block #11 (276824072) in inode 2027008.  CLEARED.
Illegal indirect block (2147483648) in inode 2027008.  CLEARED.
Illegal block #269490209 (50331648) in inode 2027008.  CLEARED.
Error storing directory block information (inode=2027008, block=0, num=158877170): Memory allocation failed


/dev/mapper/fedora_dcky--fedora--test-root: ***** FILE SYSTEM WAS MODIFIED *****
e2fsck: aborted


/dev/mapper/fedora_dcky--fedora--test-root: ***** FILE SYSTEM WAS MODIFIED *****



```

One search result suggested changing the e2fsck.conf file, and telling it to use a directory instead of memory for scratch files. I've tried that, and it still fails with the memory allocation error.  I should note that the computer only has 4 GB of RAM installed, and it's a 64-bit version of Lubuntu 12.10.

The backstory to this is, I had Lubuntu and Fedora on separate drives. I copied them both over to a 1 TB drive, which was failing. Then I purchased a new 1 TB Drive, and used dd to copy the old drive to this one. I had a kernel update in Lubuntu and it didn't "find" the Fedora partitions when it updated grub. In the past, I've had to mount the Fedora partitions and then update grub in order to get them recognized.


Here's what my e2fsck.conf file shows

```

cat /etc/e2fsck.conf
[scratch_files]
directory = /var/cache/e2fsck

```

Any help with this is greatly appreciated. I could reinstall Fedora, if necessary. But I'd like to avoid that if possible. And I could use dd to copy it from another drive, but again I'd like to avoid that also.

Have a great day, and thanks. :)
Patrick.

Also for clarification, here's the results of fdisk -l. I should note that I have three hard drives in the computer. Two that have Windows installed, and the 1TB drive with Ubuntu and Fedora installed.

```

$sudo fdisk -l


Disk /dev/sda: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00030e07


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   625137663   312465408    7  HPFS/NTFS/exFAT


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x561ad159


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1008019455   504008704   83  Linux
/dev/sdb2      1008019456  1016408063     4194304    5  Extended
/dev/sdb3      1016408064  1017432063      512000   83  Linux
/dev/sdb4      1017432064  1953523711   468045824   83  Linux
/dev/sdb5      1008021504  1016408063     4193280   82  Linux swap / Solaris


Disk /dev/sdc: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156299375 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x88cc88cc


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   156280319    78140128+   7  HPFS/NTFS/exFAT


Disk /dev/mapper/fedora_dcky--fedora--test-swap: 4160 MB, 4160749568 bytes
255 heads, 63 sectors/track, 505 cylinders, total 8126464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/fedora_dcky--fedora--test-swap doesn't contain a valid partition table


Disk /dev/mapper/fedora_dcky--fedora--test-home: 24.7 GB, 24717033472 bytes
255 heads, 63 sectors/track, 3005 cylinders, total 48275456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/fedora_dcky--fedora--test-home doesn't contain a valid partition table


Disk /dev/mapper/fedora_dcky--fedora--test-root: 50.6 GB, 50621054976 bytes
255 heads, 63 sectors/track, 6154 cylinders, total 98869248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/fedora_dcky--fedora--test-root doesn't contain a valid partition table



```

---

