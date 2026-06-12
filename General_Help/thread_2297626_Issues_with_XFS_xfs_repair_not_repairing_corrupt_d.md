---
title: "Issues with XFS: xfs_repair not repairing corrupt dinode"
date: 2015-10-05
forum: General Help
---

### Post by Jeff_Nucc on 2015-10-05
I'm having some issues with one of my XFS file systems. I'm hoping this is the correct place to post.

I get a corrupt dinode error (posted below). I'll unmount the file system and run xfs_check which will indicate issues. I'll then run xfs_repair. xfs_repair will indicate the issue is resolved. However if I run xfs_check again the corrupt dinode is still there and unrepaired.

This looked to be a bug that was fixed several years ago, yet somehow has returned?

cat /etc/os-release 
NAME="Ubuntu"
VERSION="12.04.5 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.5 LTS)"
VERSION_ID="12.04"


xfs_check and xfs_repair are version 3.1.7

cat /proc/version
Linux version 3.2.0-91-generic (buildd@lgw01-13) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #129-Ubuntu SMP Wed Sep 9 10:56:06 UTC 2015
error message:

[ 2210.287698] XFS (sdb2): corrupt dinode 332814, extent total = 1, nblocks = 0.
[ 2210.287701] ffff880e1fe36e00: 49 4e 81 a4 02 02 00 00 00 00 00 00 00 00 00 00  IN..............
[ 2210.287704] XFS (sdb2): Internal error xfs_iformat(1) at line 319 of file /build/linux-_q8eS2/linux-3.2.0/fs/xfs/xfs_inode.c.  Caller 0xffffffffa038f492
[ 2210.287705] 
[ 2210.287707] Pid: 12452, comm: searchd Tainted: G         C O 3.2.0-91-generic #129-Ubuntu
[ 2210.287709] Call Trace:
[ 2210.287722]  [<ffffffffa03496bf>] xfs_error_report+0x3f/0x50 [xfs]
[ 2210.287738]  [<ffffffffa038f492>] ? xfs_iread+0x172/0x1c0 [xfs]
[ 2210.287748]  [<ffffffffa034972e>] xfs_corruption_error+0x5e/0x90 [xfs]
[ 2210.287763]  [<ffffffffa038f1fc>] xfs_iformat+0x42c/0x550 [xfs]
[ 2210.287778]  [<ffffffffa038f492>] ? xfs_iread+0x172/0x1c0 [xfs]
[ 2210.287793]  [<ffffffffa038f492>] xfs_iread+0x172/0x1c0 [xfs]
[ 2210.287796]  [<ffffffff811960b2>] ? inode_init_always+0x102/0x1c0
[ 2210.287806]  [<ffffffffa034e1e4>] xfs_iget_cache_miss+0x64/0x220 [xfs]
[ 2210.287817]  [<ffffffffa034e4c9>] xfs_iget+0x129/0x1b0 [xfs]
[ 2210.287829]  [<ffffffffa035b88e>] xfs_lookup+0x10e/0x130 [xfs]
[ 2210.287840]  [<ffffffffa0351f91>] xfs_vn_lookup+0x51/0x90 [xfs]
[ 2210.287843]  [<ffffffff81186c55>] d_alloc_and_lookup+0x45/0x90
[ 2210.287845]  [<ffffffff81194425>] ? d_lookup+0x35/0x60
[ 2210.287848]  [<ffffffff811877af>] __lookup_hash.part.28+0xbf/0xe0
[ 2210.287850]  [<ffffffff811879da>] ? inode_permission+0x4a/0x110
[ 2210.287853]  [<ffffffff81187d30>] lookup_hash+0x50/0x60
[ 2210.287856]  [<ffffffff8118c6ab>] sys_renameat+0x18b/0x240
[ 2210.287859]  [<ffffffff8118bd92>] ? do_filp_open+0x42/0xa0
[ 2210.287861]  [<ffffffff8131fc31>] ? strncpy_from_user+0x31/0x40
[ 2210.287864]  [<ffffffff81187235>] ? putname+0x35/0x50
[ 2210.287867]  [<ffffffff8117b1fc>] ? do_sys_open+0x17c/0x240
[ 2210.287869]  [<ffffffff8117d3c5>] ? fput+0x25/0x30
[ 2210.287872]  [<ffffffff8118c77b>] sys_rename+0x1b/0x20
[ 2210.287875]  [<ffffffff8166e6e2>] system_call_fastpath+0x16/0x1b
[ 2210.287877] XFS (sdb2): Corruption detected. Unmount and run xfs_repair
[ 2210.288509] XFS (sdb2): corrupt dinode 314546, extent total = 1, nblocks = 0.
[ 2210.288512] ffff8807dfafb200: 49 4e 81 a4 02 02 00 00 00 00 00 00 00 00 00 00  IN..............
[ 2210.288515] XFS (sdb2): Internal error xfs_iformat(1) at line 319 of file /build/linux-_q8eS2/linux-3.2.0/fs/xfs/xfs_inode.c.  Caller 0xffffffffa038f492
[ 2210.288517] 
[ 2210.288519] Pid: 12452, comm: searchd Tainted: G         C O 3.2.0-91-generic #129-Ubuntu
[ 2210.288520] Call Trace:
[ 2210.288534]  [<ffffffffa03496bf>] xfs_error_report+0x3f/0x50 [xfs]
[ 2210.288549]  [<ffffffffa038f492>] ? xfs_iread+0x172/0x1c0 [xfs]
[ 2210.288559]  [<ffffffffa034972e>] xfs_corruption_error+0x5e/0x90 [xfs]
[ 2210.288574]  [<ffffffffa038f1fc>] xfs_iformat+0x42c/0x550 [xfs]
[ 2210.288589]  [<ffffffffa038f492>] ? xfs_iread+0x172/0x1c0 [xfs]
[ 2210.288605]  [<ffffffffa038f492>] xfs_iread+0x172/0x1c0 [xfs]
[ 2210.288608]  [<ffffffff811960b2>] ? inode_init_always+0x102/0x1c0
[ 2210.288618]  [<ffffffffa034e1e4>] xfs_iget_cache_miss+0x64/0x220 [xfs]
[ 2210.288629]  [<ffffffffa034e4c9>] xfs_iget+0x129/0x1b0 [xfs]
[ 2210.288641]  [<ffffffffa035b88e>] xfs_lookup+0x10e/0x130 [xfs]
[ 2210.288652]  [<ffffffffa0351f91>] xfs_vn_lookup+0x51/0x90 [xfs]
[ 2210.288655]  [<ffffffff81186c55>] d_alloc_and_lookup+0x45/0x90
[ 2210.288658]  [<ffffffff81194425>] ? d_lookup+0x35/0x60
[ 2210.288660]  [<ffffffff811877af>] __lookup_hash.part.28+0xbf/0xe0
[ 2210.288663]  [<ffffffff811879da>] ? inode_permission+0x4a/0x110
[ 2210.288665]  [<ffffffff81187d30>] lookup_hash+0x50/0x60
[ 2210.288668]  [<ffffffff8118c6ab>] sys_renameat+0x18b/0x240
[ 2210.288671]  [<ffffffff8118bd92>] ? do_filp_open+0x42/0xa0
[ 2210.288674]  [<ffffffff8131fc31>] ? strncpy_from_user+0x31/0x40
[ 2210.288677]  [<ffffffff81187235>] ? putname+0x35/0x50
[ 2210.288679]  [<ffffffff8117b1fc>] ? do_sys_open+0x17c/0x240
[ 2210.288682]  [<ffffffff8117d3c5>] ? fput+0x25/0x30
[ 2210.288684]  [<ffffffff8118c77b>] sys_rename+0x1b/0x20
[ 2210.288688]  [<ffffffff8166e6e2>] system_call_fastpath+0x16/0x1b
[ 2210.288689] XFS (sdb2): Corruption detected. Unmount and run xfs_repair

xfs_repair output:

Phase 1 - find and verify superblock...
        - block cache size set to 5896280 entries
Phase 2 - using internal log
        - zero log...
zero_log: head block 3062550 tail block 3062550
        - scan filesystem freespace and inode maps...
        - found root inode chunk
Phase 3 - for each AG...
        - scan and clear agi unlinked lists...
        - process known inodes and perform inode discovery...
        - agno = 0
data fork in regular inode 34486 claims used block 2425385221
correcting nblocks for inode 53976, was 0 - counted 5
data fork in regular inode 314546 claims used block 4026531936
data fork in regular inode 332814 claims used block 2952791222
correcting nblocks for inode 332814, was 1 - counted 0
data fork in regular inode 332900 claims used block 2952791223
correcting nblocks for inode 332900, was 1 - counted 0
data fork in regular inode 332945 claims used block 2952791224
correcting nblocks for inode 332945, was 1 - counted 0
data fork in regular inode 333047 claims used block 2952791225
correcting nblocks for inode 333047, was 1 - counted 0
data fork in regular inode 333082 claims used block 2952791226
correcting nblocks for inode 333082, was 1 - counted 0
        - agno = 1
        - agno = 2
        - agno = 3
        - agno = 4
        - agno = 5
        - agno = 6
        - agno = 7
        - agno = 8
        - agno = 9
        - agno = 10
        - agno = 11
        - agno = 12
        - agno = 13
        - agno = 14
        - agno = 15
        - agno = 16
        - agno = 17
        - process newly discovered inodes...
Phase 4 - check for duplicate blocks...
        - setting up duplicate extent list...
        - check for inodes claiming duplicate blocks...
        - agno = 0
        - agno = 4
        - agno = 8
        - agno = 17
        - agno = 3
        - agno = 1
        - agno = 5
        - agno = 6
        - agno = 7
        - agno = 2
        - agno = 10
        - agno = 9
        - agno = 11
        - agno = 13
        - agno = 12
        - agno = 14
        - agno = 15
        - agno = 16
data fork in regular inode 34486 claims used block 2425385221
data fork in regular inode 314546 claims used block 4026531936
data fork in regular inode 332814 claims used block 2952791222
data fork in regular inode 332900 claims used block 2952791223
data fork in regular inode 332945 claims used block 2952791224
data fork in regular inode 333047 claims used block 2952791225
data fork in regular inode 333082 claims used block 2952791226
Phase 5 - rebuild AG headers and trees...
        - agno = 0
        - agno = 1
        - agno = 2
        - agno = 3
        - agno = 4
        - agno = 5
        - agno = 6
        - agno = 7
        - agno = 8
        - agno = 9
        - agno = 10
        - agno = 11
        - agno = 12
        - agno = 13
        - agno = 14
        - agno = 15
        - agno = 16
        - agno = 17
        - reset superblock...
Phase 6 - check inode connectivity...
        - resetting contents of realtime bitmap and summary inodes
        - traversing filesystem ...
        - agno = 0
        - agno = 1
        - agno = 2
        - agno = 3
        - agno = 4
        - agno = 5
        - agno = 6
        - agno = 7
        - agno = 8
        - agno = 9
        - agno = 10
        - agno = 11
        - agno = 12
        - agno = 13
        - agno = 14
        - agno = 15
        - agno = 16
        - agno = 17
        - traversal finished ...
        - moving disconnected inodes to lost+found ...
Phase 7 - verify and correct link counts...

        XFS_REPAIR Summary    Wed Sep 16 13:16:04 2015

Phase        Start        End        Duration
Phase 1:    09/16 13:15:52    09/16 13:15:52    
Phase 2:    09/16 13:15:52    09/16 13:15:55    3 seconds
Phase 3:    09/16 13:15:55    09/16 13:16:03    8 seconds
Phase 4:    09/16 13:16:03    09/16 13:16:04    1 second
Phase 5:    09/16 13:16:04    09/16 13:16:04    
Phase 6:    09/16 13:16:04    09/16 13:16:04    
Phase 7:    09/16 13:16:04    09/16 13:16:04    

Total run time: 12 seconds
done

---

### Post by Jeff_Nucc on 2015-10-08
xfs_repair was an older version with Ubuntu 12.xx. THis issue was fixed in newer versions of xfs_repair.  I obtained updated code from git and built it. The newer xfs_repair xorrected the issue.

---

