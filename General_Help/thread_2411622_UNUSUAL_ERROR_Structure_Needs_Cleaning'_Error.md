---
title: "UNUSUAL ERROR: Structure Needs Cleaning' Error"
date: 2019-02-01
forum: General Help
---

### Post by lubomier.sk on 2019-02-01
Hello,
when I'm trying to mount EXT4 filesystem under  Ubuntu 18.04.1 LTS I'm getting this:
```
[FONT=courier new]
[SIZE=3]mount  /dev/mapper/crypto--vg-storage--lv /mnt/storage/[/SIZE][/FONT][SIZE=3][FONT=courier new]
mount: /mnt/storage: mount(2) system call failed: Structure needs cleaning.[/FONT][/SIZE]

```

Of course I googled  related issues, but mostly about files. And pointed to the the same answer [B]fsck

[/B]```
[SIZE=3][FONT=courier new]fsck /dev/mapper/crypto--vg-storage--lv [/FONT]
[FONT=courier new]fsck from util-linux 2.31.1[/FONT]
[FONT=courier new]e2fsck 1.44.1 (24-Mar-2018)[/FONT]
[FONT=courier new]storage: clean, 1509918/94252288 files, 323610962/432799744 blocks[/FONT][/SIZE]

```

Even forced cleanup ... (first run found some inodes and were fixed)

```
[SIZE=3][FONT=courier new]fsck -Vf /dev/mapper/crypto--vg-storage--lv [/FONT]
[FONT=courier new]fsck from util-linux 2.31.1[/FONT]
[FONT=courier new][/sbin/fsck.ext4 (1) -- /dev/mapper/crypto--vg-storage--lv] fsck.ext4 -f /dev/mapper/crypto--vg-storage--lv [/FONT]
[FONT=courier new]e2fsck 1.44.1 (24-Mar-2018)[/FONT]
[FONT=courier new]Pass 1: Checking inodes, blocks, and sizes[/FONT]
[FONT=courier new]Pass 2: Checking directory structure[/FONT]
[FONT=courier new]Pass 3: Checking directory connectivity[/FONT]
[FONT=courier new]Pass 4: Checking reference counts[/FONT]
[FONT=courier new]Pass 5: Checking group summary information[/FONT]
[/SIZE][FONT=courier new][SIZE=3]storage: 1509918/94252288 files (0.6% non-contiguous), 323610962/432799744 blocks[/SIZE]
[/FONT]
```

But still mount complains same way. Even I've checked that filesystem is clean and healthy because:
1.
```
[SIZE=3][FONT=courier new]tune2fs -l /dev/mapper/crypto--vg-storage--lv | grep state[/FONT]
[FONT=courier new]Filesystem state:         clean[/FONT][/SIZE]

```

2. debugfs can access FS and list files as well...

3. Was successfully mounted under Tails and UBUNTU Live 18.10. Files were accessible without any issues

My current system is up-to-date. My complete stack is: RAID, LUKS, LVM2, EXT4

Thanks for any ideas.

---

