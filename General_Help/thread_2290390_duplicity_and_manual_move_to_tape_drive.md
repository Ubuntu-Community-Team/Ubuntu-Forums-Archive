---
title: "duplicity and manual move to tape drive"
date: 2015-08-12
forum: General Help
---

### Post by oli004 on 2015-08-12
Hi,

I am trying to do the following:

1. Backup the data on an ubuntu server to a local drive using duplicity, by
      - automatically making a full backup every 14 days and
      - automatically making incremental backups every 4 hours

2. Every month or so, I would like to move the old backup files to a tape drive, by manually moving the files. 
(mv /path-to-local-backup/files-older-than-current-full-backup* /tape-drive)

Is that doable?
Can I just move the old backup files (full and incremental) which are older than the last full backup, to a different location? Or will that destroy the backups' or duplicity's integrity in some way?
Do I have to consider anything when doing this?

Thanks for your insight.

Greetings

Oli4

---

### Post by papibe on 2015-08-12
Hi oli004. Welcome to the forum ):P

Incremental backups need to look at all the past incrementals and back to the latest full backup.

Considering that, you should be able to move/delete anything before the last full backup (excluding it).

Having said that, I would copy that data, not move, and then I would let duplicity itself to remove the old backups by using the 'remove-older-than' command. For instance:
```
duplicity remove-older-than 15D --force /path-to-local-backup/
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by oli004 on 2015-08-12
Hi papibe,

thanks for your nice welcome and for removing the brick in my head :-).

Your solution is absolutely the safest way and exactely how I will do it.

Greetings from Germany

Oli4

---

