---
title: "How do I back up a ZFS filesystem properly?"
date: 2016-09-25
forum: General Help
---

### Post by courtney2 on 2016-09-25
I currently have a ZFS filesystem on drive /dev/sdb with live LXC containers and I want to know what a good way is to back them up. I've looked at other answers and solutions seem to be unexplained and confusing, or aren't similar to my need. I already have an external HDD that I have set up with a ZFS storage pool on it, and I kind of like the idea of doing an rsync, because to my understanding, the zfs send command people use only creates a single file, which, if it gets corrupted, my backup is ruined. What I don't know is where to find my zfs pool (on /dev/sdb) in my filesystem to select it, the proper rsync command to issue to do the backups, and if I had to restore my pool, how would I do that from my external drive?

---

### Post by TheFu on 2016-09-25
rsync is an amazing tool, but not for versioned backups, IMHO. For that, use rdiff-backup - it has a very similar command style to rsync, but does versioned files.  I keep 60 days of backups on low-risk systems and those take about 1.2x the original storage.  Basically, if my OS is 10G, then having 60 days of versioned backups requires 12G.  Plus the most recent backup looks like an rsync mirror, which I love.

Best intro to rdiff-backup that I know: [https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/)

---

