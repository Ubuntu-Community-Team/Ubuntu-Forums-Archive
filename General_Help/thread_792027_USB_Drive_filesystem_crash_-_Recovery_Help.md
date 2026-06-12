---
title: "USB Drive filesystem crash - Recovery Help"
date: 2008-05-12
forum: General Help
---

### Post by TheForkOfJustice on 2008-05-12
My USB drive seems to have had a major crash that pooched some important data so I'm trying to do a recovery.

Before the crash (or during it as the case may be) I noticed that copying entire directories for backup was getting warning saying that I didn't have the right permissions to copy these files which was silly.

I cut the drive into two 40GB partitions, both with ext3 filesystems.

I ran fsck to hopefully fix the problem with the following results:

- The journaling information has been dropped so the FS is now apparently ext2
- fsck stops running after some time and will not continue even if left for hours by itself so I can't complete a full scan of the partitions.
- no luck in recovering the drives.
- if the partitions mount it will likely say that I do not have the permissions needed to access them 

That's about it.  Any help you all can offer is appreciated.

---

