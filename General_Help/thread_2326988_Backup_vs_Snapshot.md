---
title: "Backup vs Snapshot"
date: 2016-06-06
forum: General Help
---

### Post by uwe-bungto on 2016-06-06
I have over 20,000 files, Photos + .XMP which need to be backed up on a new HDD.
I already have backups which were mainly done manually at the time of transferring photos from the SD cards and at the time of editing.

Since I am starting with a new HDD what would be the better method? Using Unison or using Backintime?

I have used both, Unison for syncing computers and Backintime for snapshots, and like both.
What are the pros/cons of each?
Thanks

Paul

---

### Post by Fire_Chief on 2016-06-07
Unison will simply keep the target files in sync with the source files. So if you make changes to the source file, that is replicated to the target and the old version of the file is gone. It's not really a backup tool as much as a sync tool.
Backintime is able to keep historical versions of files as they change and store the current version and the old versions in a target location. The snapshot term is just semantics for "can restore an older version of a file before it was changed". It also can run on a schedule to perform regular backups (take snapshots) of the current state of data.

If you're just looking for a way to duplicate your file archives (data that doesn't get changed anymore), then either tool is fine but Unison will setup easier. For that matter, you could use any file copy tool to duplicate the files into the new hard drive.

---

### Post by uwe-bungto on 2016-06-07
Thanks. I think I'll go with backintime, if I decide that one of those photos I deleted last week should not have been I can retrieve it.

---

