---
title: "Delete zero byte files except the newest"
date: 2018-08-17
forum: General Help
---

### Post by raleigh3 on 2018-08-17
I use this to make it easy to see when a directory has been updated.

```
touch /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/$( date '+%m-%d-%Y_%I:%M-%p' )
```

How can I get it to delete the older files while leaving the newest?

---

### Post by TheFu on 2018-08-17
You can't be vague on what "older" and "newer" mean.   10 days or older?  Only keep most recent 3 files?  You need to be specific.  Google will find lots of solutions for both.  The older than Y days method is easiest.   

If they are log files, you really should use **logrotate** to manage them. Don't reinvent the wheel.

If they are backup files, a proper backup tool will have an option to remove old backup sets.

---

### Post by raleigh3 on 2018-08-17
My command creates a 0 byte file with the date and time as it's name.

08-17-2018_03:22-PM

My backup script creates them in directories to which files are copied to.

If I do nothing more, I will have a buildup of those files.

I want to delete all but the newest one.

---

### Post by TheFu on 2018-08-17
Remember when I suggested using yyyy-mm-dd to help make sorting easier? There was a good reason.   If you use that format, then you can sort and remove all but the last one. Might I suggest you keep the last 3 instead?  Some versioning is important for backups.

$ date "+%F"

But using a backup tool for this would make life so much easier.

Or you could just leave them around a few weeks and delete them after 15 days have passed.  That's easy with find.
```
$ find /full/path/to/directory -type f -size 0 -mtime +15 -delete
``` Drop this into the explainshell.com to see what it does if you need to.

---

### Post by sisco311 on 2018-08-17
For some hints check out BashFAQ 003 and 099 (link in my signature).

Why don't you delete the old files before you create the new one? :confused:

---

