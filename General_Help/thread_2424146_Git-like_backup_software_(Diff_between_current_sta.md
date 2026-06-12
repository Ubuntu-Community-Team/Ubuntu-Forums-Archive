---
title: "Git-like backup software? (Diff between current state and a backup)"
date: 2019-08-04
forum: General Help
---

### Post by Datoyminaytah on 2019-08-04
Git would be great for incremental backups, and comparing diffs between current state and backups, except by design it doesn't store ownership/group/attribute information.

Is there any backup software that works similarly to git? Either command line or gui.

It doesn't have to be based on git, or use the same commands, just...

- Show list of differences between current state and some backup, or between two backups
- Show changes to ownership, attributes, size, modification date, etc. for all files that are different
- Show diff for text-type files
- Preferably, store all changes as diffs/patches, like git, for compactness of data

I've looked around and haven't seen anything yet.

---

### Post by Holger_Gehrke on 2019-08-04
[rdiff-backup]("http://rdiff-backup.nongnu.org/") ? It's in the repos.

Holger

---

### Post by GhX6GZMB on 2019-08-04
I use TimeShift.
[https://github.com/teejee2008/timeshift](https://github.com/teejee2008/timeshift)

Works perfectly, it's based on rsync. An initial backup is created with all files, subsequent backups contain hard links to the previous state if unchanged. By default, root and home directories are excluded to avoid overwriting updates and user files when restoring, but this can be changed as needed.

---

### Post by Datoyminaytah on 2019-08-05
Both of those sound good. Seems like rdiff-backup would require less space in the long run.

If I'm reading correctly, rdiff-backup stores the full files of the latest backup, with "reverse diffs" ("patches" from current to previous, previous to next previous, etc.)

Another issue I'm interested in, is how to deal with changes in how partitions are mounted, including bind mounts. I suppose if you're just backing up "/" it would back up the files by path irrespective of how things are mounted. But if fstab is backed up before and after you have moved around partitions, you would have to be very careful when restoring to a point before when you changed partitions. Right?

I'm still setting up my system. I have an SSD but am not using it yet until things are fairly stable. So I'll definitely be rearranging partitions in the future. But in the meantime, I need backup in case my configuration "breaks" the system (which has nearly happened a few times already.)

---

