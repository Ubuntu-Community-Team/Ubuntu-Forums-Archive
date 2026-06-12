---
title: "Help recovering lost partition"
date: 2024-06-27
forum: General Help
---

### Post by romprod on 2024-06-27
Hi,

I'm looking for assistant with recovering a lost partition. In a moment of madness while trying to expand the partition I appear to have lost my ext4 partition and now I'm unable to mount the partition and I'm in below my depth!

I took a bunch of screenshots and took details before I managed to break it.

Can anyone advise me the best way forward please so that I don't lose my data?

This was the partition originally which I believe this information can be used to re-create the ext4 partition?

```
Disk /dev/sdb1: 791.02 GiB, 849346560000 bytes, 1658880000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xbb4113f3
```

as well as this
```

Unpartitioned space /dev/sdb1: 791.01 GiB, 849345511424 bytes, 1658877952 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Start        End    Sectors  Size
 2048 1658879999 1658877952  791G
```

When I try to re-mount the partition I get the following

```
mount /hdd
mount: /hdd: special device /dev/disk/by-uuid/253ac7df-2809-4d69-802b-7e9c1c5e1a03 does not exist.
```

```
linuxserver01:~$ sudo blkid
/dev/sda2: UUID="aa0d18d3-19da-4f99-91af-50d67e58e1f6" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="1d2a23f1-15c9-4d49-b4b6-5cddbf6c61d2"
/dev/loop1: TYPE="squashfs"
/dev/sdb1: PTUUID="8d734eb1" PTTYPE="dos" PARTUUID="1d5e5153-a6c6-6b43-863e-df1fe4f0d217"
/dev/loop4: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop0: TYPE="squashfs"
/dev/sda1: PARTUUID="81a89fdc-5be0-46df-9520-07d99b019aeb"
/dev/loop5: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"

```

```
sudo mount /dev/disk/by-partuuid/1d5e5153-a6c6-6b43-863e-df1fe4f0d217 /hdd
mount: /hdd: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error.

```

---

### Post by aljames2 on 2024-06-27
For more background, can you talk about what you were doing to “expand the partition”.  What command(s) did you run, etc.

Did you try a more basic mounting command like:
```
sudo mount /dev/sdb1 /mnt
```

Don’t panic or do anything more other than provide facts here and give time for folks to respond.

---

### Post by romprod on 2024-06-28
I had tried sudo mount /dev/sdb1 /mnt but had a similar error message, I forgot to include it in my original post, sorry. Thankyou for your advice.

But good news, I ran the following command and voila, I have my data back, it mounted immediately.

```
fsck -t ext4 /dev/sdb1
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
ext2fs_open2: Bad magic number in super-block
fsck.ext4: Superblock invalid, trying backup blocks...
/dev/sdb1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(204800000--204986340) -(204986368--204996607) -(205029376--205032426) -(205033472--205357055) -(205357088--205359034) -(205359104--205392798) -(205393920--205520895) -(205553664--205772690) -(205772800--205778483) -(205778944--205785025) -(205785088--206045183) -(206077952--206308324) -(206308357--206309354) -(206309376--206323645) -(206323712--206327748) -(206327808--206332977) -(206333952--206551039) -(206551072--206551620) -(206553088--206569471) -(206602240--206788579) -(206788608--206792639) -(206792704--206799839) -(206800896--207093759) -(207126528--207228863) -(207228928--207259357) -(207259648--207263688) -(207263744--207355903)
Fix<y>? yes
Free blocks count wrong for group #0 (2535, counted=2528).
Fix<y>? yes
Free blocks count wrong for group #594 (0, counted=19).
Fix<y>? yes
Free blocks count wrong for group #595 (0, counted=19).
Fix<y>? yes
Free blocks count wrong for group #5465 (1800, counted=1818).
Fix<y>? yes
Free blocks count wrong for group #5471 (2404, counted=2426).
Fix<y>? yes
Free blocks count wrong for group #5495 (1308, counted=1322).
Fix<y>? yes
Free blocks count wrong for group #5496 (1990, counted=1974).
Fix<y>? yes
Free blocks count wrong for group #5498 (888, counted=869).
Fix<y>? yes
Free blocks count wrong for group #5499 (851, counted=832).
Fix ('a' enables 'yes' to all) <y>? yes
Free blocks count wrong for group #5850 (4112, counted=4125).
Fix ('a' enables 'yes' to all) <y>? yes
Free blocks count wrong for group #5861 (917, counted=897).
Fix ('a' enables 'yes' to all) <y>? yes
Free blocks count wrong for group #5970 (1646, counted=1615).
Fix ('a' enables 'yes' to all) <y>? yes to all
Free blocks count wrong for group #5999 (15810, counted=15803).
Fix? yes

Free blocks count wrong for group #6006 (28743, counted=28739).
Fix? yes

Free blocks count wrong (7365154, counted=7365136).
Fix? yes

Inode bitmap differences:  -(51773441--51830784)
Fix? yes

Free inodes count wrong for group #320 (0, counted=3).
Fix? yes

Free inodes count wrong for group #736 (7447, counted=7445).
Fix? yes

Free inodes count wrong (51308514, counted=51308515).
Fix? yes

Padding at end of inode bitmap is not set. Fix? yes


/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdb1: 538653/51847168 files (4.0% non-contiguous), 199994864/207360000 blocks

```

---

### Post by aljames2 on 2024-06-28
Great, now before you have coffee, make a backup (I would make 2), on a separate storage device(s). Consider this a lucky draw.  That device could be on the way out.

---

