---
title: "Switching drive for backup storage"
date: 2022-04-11
forum: General Help
---

### Post by sofasurfer on 2022-04-11
I am moving my back-in-time backup destination from drive 'A' to drive 'B'. I want to remove drive 'A'. If I change the destination and do a new snapshot, will the new snapshot be incremental or full? Or should I delete the snapshots on drive 'A' before I do a new snapshot on drive 'B'?

---

### Post by psychohermit on 2022-04-11
I would think you want it to be full as he other drive will no longer exist for an incremental.  I would delete snapshots on drive A to force a full snapshot just to be sure.

Just my $0.02

--glenn

---

### Post by sofasurfer on 2022-04-11
I removed the old drive and then did the backup on the new drive. Seems to be ok. 
Another thought, if anyone cares to answer, If I have a collection of snapshots and I delete the first few so that the original full snapshot is missing and then do another snapshot, will a new full snapshot be forced to be created?

---

### Post by deadflowr on 2022-04-11
Most incremental backup utilities require the original full backup to still exist.
They usually also require all preceding incremental backups before the current incremental backup to still exist.
This is because incremental backups are usually very tiny and sometimes don't even backup the full file that a change might have been made in.
So any previous backups, starting from the full backup, might be required in order for any new backups to make any sense to the backup utility.

---

### Post by vanadium on 2022-04-13
> **deadflowr said:**
> Most incremental backup utilities require the original full backup to still exist.
They usually also require all preceding incremental backups before the current incremental backup to still exist.

Not so with back-in-time (at least with rsync, I do not know how it works with btrfs). Any snapshot is a full selfcontained file system. You can delete any other snapshot, and your left snapshot will be untouched.

That is because back-in-time works (through rsync) with hard links to link to a copy in a previous snapshot that was not changed. Thus, the same file data on disk is referenced from different places in the file system.

Every hard link in linux is equivalent. Every hard link points to the same inode, which in turn refers to the data on disk. The data remains accessible until the last remaining hard link has been deleted.

Creating a snapshot on a different drive automatically will effectively transfer all of the data the first time. Subsequent times, unchanged data of the previous snapshot will be hard linked.

---

### Post by TheFu on 2022-04-13
Back-in-time uses rsync + hardlinking to work.  You can remove any of the snapshots you like. Learn about hardlinks to understand the nuts and bolts for how this actually works.  Wikipedia has an article about hardlinks.

There are some limitations that are important to know too.

---

