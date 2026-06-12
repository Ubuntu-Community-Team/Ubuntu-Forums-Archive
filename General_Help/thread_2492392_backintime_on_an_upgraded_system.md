---
title: "backintime on an upgraded system"
date: 2023-11-09
forum: General Help
---

### Post by syrag on 2023-11-09
I upgraded from 18.04 to 20.04. When I back up the new system with backintime (home directory, /root, /var/lib, and 1.4 TB of photos) it does a new snapshot, rather than an incremental backup. I don't need and don't want this.
The old backups are present, and 'check-config' says everything is fine.
Is there a way I can tell backintime to just look at the upgraded system as incrementally changed, and not have take a new 1.XX TB snapshot?

---

### Post by syrag on 2023-11-12
Found the answer [here]("https://github.com/bit-team/backintime#file-permissions-handling-and-therefore-possible-non-differential-backups"):

> In version 1.2.0, the handling of file permissions changed. In versions <= 1.1.24 (until 2017) all file permissions were set to -rw-r--r-- in the backup target. In versions >= 1.2.0 (since 2019) rsync is executed with --perms option which tells rsync to preserve the source file permission.

Therefore backups can be larger and slower, especially the first backup after upgrading to a version >= 1.2.0.

If you don't like the new behavior, you can use Expert Options -> Paste additional options to rsync to add --no-perms --no-group --no-owner to it. Note that the exact file permissions can still be found in fileinfo.bz2 and are also considered when restoring files.

---

