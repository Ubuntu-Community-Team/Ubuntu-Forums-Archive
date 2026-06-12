---
title: "RSync (Luckybackup) - Same Data - New Source Location - How To??"
date: 2019-02-07
forum: General Help
---

### Post by 777funk on 2019-02-07
I'm in the process of migrating TeraBytes of data to a new drive. All of this data is already backed up on my backup HDD (the destination). Is there a way to adjust where RSync (LuckyBackup) looks to find the data source? It will of course think it's all fresh data simply because it's in a new location but it's what I've had backed up for years. How do I tell it that it's my old data, just new source location? 

Seems like this would be a fairly common problem to have.

---

### Post by dmnur on 2019-02-08
For rsync manual:
> Normally rsync will skip any files that are already the same size and have the same modification timestamp.
It doesn't know what source was previously used. Even that there were previous iterations at all.
In other words, rsync itself doesn't store any state information, so it won't break anything.

luckyBackup uses plain rsync, so no problem with it too. Just modify the task and replace your old source with the new one.

A simple test with plain rsync:
```

$ mkdir tmp
$ cd tmp
$ mkdir backup

# old drive
$ mkdir old
$ echo one > old/one
$ echo two > old/two

# backing up old drive: 2 new files
$ rsync -a --delete-after --stats old/ backup/
Number of files: 3 (reg: 2, dir: 1)
Number of created files: 2 (reg: 2)
Number of deleted files: 0
...

# copying old data to a new drive (modification times are preserved)
$ rsync -a old/ new/

# backing up new drive: nothing changed
$ rsync -a --delete-after --stats new/ backup/
Number of files: 3 (reg: 2, dir: 1)
Number of created files: 0
Number of deleted files: 0
Number of regular files transferred: 0
...

# but if we change some file's modification time...
$ touch new/one

# backing up new drive again: 1 "new" file
$ rsync -a --delete-after --stats new/ backup/
Number of files: 3 (reg: 2, dir: 1)
Number of created files: 0
Number of deleted files: 0
Number of regular files transferred: 1
...

```

Also, rsync has the *--dry-run* option, and luckyBackup has the corresponding checkbox ("Dry"). Just use them for testing: every change will be listed, but not actually applied.

---

