---
title: "LUKS partition shrinking broke the filesystem inside"
date: 2014-01-29
forum: General Help
---

### Post by chojnacki-pawel on 2014-01-29
Hello to everybody on the Forums!

Yesterday I tried to shrink my LUKS-encrypted /dev/sdb5 partition from 119 to 110 GB according to [http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724) . Each step worked properly, but in the end I'm not able to mount the partition:

```
# cryptsetup luksOpen /dev/sdb5 neuro
```

accepts the proper password, doesn't recognize any other, and fails to mount the partition inside:

```
# mount /dev/mapper/neuro /mnt/
mount: unknown filesystem type 'LVM2_member'

# lvdisplay
  --- Logical volume ---
  LV Path                /dev/xubuntu-vg/root
  LV Name                root
  VG Name                xubuntu-vg
  LV UUID                WjTjmo-j1FO-vDej-QE5X-Qym6-DanB-B8Bnhx
  LV Write Access        read/write
  LV Creation host, time xubuntu, 2013-06-03 21:57:17 +0200
  LV Status              suspended
  # open                 0
  LV Size                110.00 GiB
  Current LE             28160
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:4

# pvdisplay
  --- Physical volume ---
  PV Name               /dev/mapper/neuro
  VG Name               xubuntu-vg
  PV Size               110.01 GiB / not usable 1.24 MiB
  Allocatable           NO
  PE Size               4.00 MiB
  Total PE              28162
  Free PE               2
  Allocated PE          28160
  PV UUID               3qmIAm-TFhv-ZzJQ-DLXR-SUPI-5CF8-V6JB6I


# fdisk -l /dev/sdb

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d0d6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      499711      248832   83  Linux
/dev/sdb2          499712   230709585   115104937    5  Extended
/dev/sdb5          501760   230709585   115103913   83  Linux

# fdisk -l /dev/mapper/neuro

Disk /dev/mapper/neuro: 117.9 GB, 117864309760 bytes
255 heads, 63 sectors/track, 14329 cylinders, total 230203730 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/neuro doesn't contain a valid partition table
```

As far as I understand, the physical volume is 110 GB large, and filesystem is 117.9 GB (why?). When trying to read from superblocks:

```
# fsck.ext4 /dev/mapper/neuro
e2fsck 1.42.9 (28-Dec-2013)
ext2fs_open2: Bad magic number in super-block
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/mapper/neuro

# mke2fs -n /dev/mapper/neuro
mke2fs 1.42.9 (28-Dec-2013)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
7200768 inodes, 28775466 blocks
1438773 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
879 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
    4096000, 7962624, 11239424, 20480000, 23887872

```
When trying to replace any of the listed superblocks:

```
# fsck.ext4 -b 32768 /dev/mapper/neuro
e2fsck 1.42.9 (28-Dec-2013)
fsck.ext4: Bad magic number in super-block while trying to open /dev/mapper/neuro
```

Testdisk recognizes the filesystem as FAT32 and can't do much. Photorec on the other hand can seamlessly recover all data as long as it's told that the filesystem is ext4.

From what I understand, the first stem in the resizing process - resize2fs -p /dev/mapper/neuro-root 9G - has gone wrong - even though all the tests done in the meantime worked.

I have a backup from 3 days ago, yet it's a question of honor for me to understand what has gone wrong and how to repair it. Can you please help me?

---

