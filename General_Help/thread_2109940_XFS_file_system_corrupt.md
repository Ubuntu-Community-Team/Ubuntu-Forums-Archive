---
title: "XFS file system corrupt"
date: 2013-01-28
forum: General Help
---

### Post by Kissell on 2013-01-28
I am trying to delete some files, and it says:
> rm: cannot remove `picture.png': Structure needs cleaning

I unmount the volume and run xfs_repair, even with the -L option, then mount the volume...  but still I cannot delete that file.

How can I force XFS to repair?

xfs_repair -L /dev/mapper/Data
> 
Phase 1 - find and verify superblock...
Phase 2 - using internal log
        - zero log...
        - scan filesystem freespace and inode maps...
        - found root inode chunk
Phase 3 - for each AG...
        - scan and clear agi unlinked lists...
        - process known inodes and perform inode discovery...
        - agno = 0
data fork in regular inode 4497195 claims used block 4832288037
data fork in regular inode 349982619 claims used block 4832288030
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
        - agno = 18
        - agno = 19
        - agno = 20
        - process newly discovered inodes...
Phase 4 - check for duplicate blocks...
        - setting up duplicate extent list...
        - check for inodes claiming duplicate blocks...
        - agno = 0
        - agno = 1
        - agno = 3
        - agno = 7
        - agno = 8
        - agno = 9
        - agno = 10
        - agno = 11
        - agno = 12
        - agno = 6
        - agno = 14
        - agno = 4
        - agno = 5
        - agno = 16
        - agno = 2
        - agno = 19
        - agno = 20
        - agno = 13
        - agno = 17
        - agno = 18
        - agno = 15
data fork in regular inode 4497195 claims used block 4832288037
data fork in regular inode 349982619 claims used block 4832288030
Phase 5 - rebuild AG headers and trees...
        - reset superblock...
Phase 6 - check inode connectivity...
        - resetting contents of realtime bitmap and summary inodes
        - traversing filesystem ...
        - traversal finished ...
        - moving disconnected inodes to lost+found ...
Phase 7 - verify and correct link counts...
done


---

### Post by Kissell on 2013-01-28
Very hesitantly, I ran xfs_db on the two inodes that xfs_repair complained about.  Then ran xfs_repair again, and this time it didn't mention them....   and now I can delete the files I could not delete before...

Hopefully nothing else is missing...


xfs_db -x -c 'inode 4497195' -c 'write core.nextents 0' -c 'write core.size 0' /dev/mapper/Data
> 
core.nextents = 0
core.size = 0


xfs_db -x -c 'inode 349982619' -c 'write core.nextents 0' -c 'write core.size 0' /dev/mapper/Data
> 
core.nextents = 0
core.size = 0


---

