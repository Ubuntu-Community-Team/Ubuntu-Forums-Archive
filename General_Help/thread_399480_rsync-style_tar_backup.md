---
title: "rsync-style tar backup"
date: 2007-04-02
forum: General Help
---

### Post by cookfromfrozen on 2007-04-02
Hi
I have a 16 gigabyte home directory.  To backup I am currently tar'ring it up, but this takes a long time since it backs up everything regardless of whether it has changed or not since the last backup.

Is there any way to get tar to work like rsync, in that it only backs up what has changed since last time (and deletes files that have disappeared since)?

---

### Post by H3g3m0n on 2007-04-02
> **man tar said:**
> 
       -G, --incremental
              create/list/extract old GNU-format incremental backup

       -g, --listed-incremental F
              create/list/extract new GNU-format incremental backup

...

       -N, --after-date DATE, --newer DATE
              only store files newer than DATE

       --newer-mtime DATE
              only store files whose contents have changed after DATE

Otherwise googling tar incremental backup should give you examples.

Alternatively you could just use rsync, it will work locally, the files won't be in one archive though.

---

