---
title: "Ubuntu won't boot - /run corruption"
date: 2018-03-23
forum: General Help
---

### Post by sonicwind on 2018-03-23
Since we started receiving Spectre/Meltdown updates, I've been getting critical errors such as the following:

```
EXT4-fs (sda1): Delayed block allocation failed for inode 1218997 at logical offset 248 with max blocks 3 with error 12190427
EXT4-fs (sda1): This should not happen!! Data will be lost
```

I had one file in lost+found and a find by inode showed the file as /run/user/1000/gvfs.

Yesterday the system didn't boot at all and this is what it said:

```
EXT4-fs error (device sda1): htree_dirblock_to_tree: inode 12190427: block 48767527: comm apt-config: bad entry in directory: rec_len is smaller than minimal - offset=0(4096), inode=0, rec_len=0, name_len=0
Aborting journal on device sda1-8.
EXT4-fs (sda1): Remounting filesystem read-only
EXT4-fs error (device sda1): ext4_journal_check_start: 56: Detected aborted journal
```

I got an initramfs prompt and did an FSCK. It did its thing and I'm now where I can't get past a low graphics mode screen.

To be clear, from a Live DVD: SMART results are OK, an FSCK shows a clean file system and all the now dozens of files in my lost+found have been virtual ( /run ) files that no longer exist.

I've tried two different kernels (4.10.0-42 & 4.13.0-37). Same issues.

I did a Boot Repair from Live DVD but it found nothing wrong. [https://paste.ubuntu.com/p/TW5DdPxGZ2/](https://paste.ubuntu.com/p/TW5DdPxGZ2/)

I ran the MemTest for 10 passes/13 hours and no bad RAM found.

Ubuntu 16.04 LTS is the only OS. 6MB RAM
Intel i3-2120 with 2nd Generation Integrated Graphics

Any ideas? Thank you so much for your help.

---

