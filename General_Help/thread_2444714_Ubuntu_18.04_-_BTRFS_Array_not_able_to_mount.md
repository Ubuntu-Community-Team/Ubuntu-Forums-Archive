---
title: "Ubuntu 18.04 - BTRFS Array not able to mount"
date: 2020-06-03
forum: General Help
---

### Post by staudamm on 2020-06-03
Hi all

My small home server stopped booting yesterday due to an error in the filesystem of my raid array.
Setup:
Ubuntu 18.04 on Disk 1 via SATA
BTRFS array via LSI 9460 Raid controller which managed Raid 6

Main error is:
'parent transid verify failed on ### wanted ## found ##

The following steps have been taken:
[LIST]
[*]I tried mounting the drive manually as read-only as explained in [THIS]("https://askubuntu.com/questions/157917/how-do-i-recover-a-btrfs-partition-that-will-not-mount") post, which didn't work.
[*]btrfs restore <source> <dest> as in the same post worked
[*]btrfs rescue zero-log /dev/## failed with message:
[/LIST]

btrfs rescue zero-log /dev/sda
parent transid verify failed on 30507008 wanted 142536 found 142537
parent transid verify failed on 30507008 wanted 142536 found 142537
parent transid verify failed on 30507008 wanted 142536 found 142537
parent transid verify failed on 30507008 wanted 142536 found 142537
Ignoring transid failure
Clearing log on /dev/sda, previous log_root 0, level 0
parent transid verify failed on 13346641330176 wanted 142536 found 142538
Ignoring transid failure
leaf parent key incorrect 13346641330176
transaction.c:76: update_cowonly_root: BUG_ON `ret` triggered, value -1
btrfs(+0x3cde2)[0x56268caefde2]
btrfs(commit_tree_roots+0x121)[0x56268caefffd]
btrfs(btrfs_commit_transaction+0xb9)[0x56268caf0206]
btrfs(+0x57803)[0x56268cb0a803]
btrfs(main+0x143)[0x56268cac9c87]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xe7)[0x7f26ff2ecb97]
btrfs(_start+0x2a)[0x56268cac9cca]
Aborted


Obviously the right question is, if anyone has another idea to save this case.

Regards

---

