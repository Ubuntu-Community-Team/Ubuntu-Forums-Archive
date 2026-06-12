---
title: "Quickly find if any file exists with new timestamp"
date: 2013-07-11
forum: General Help
---

### Post by Kissell on 2013-07-11
I've got a cron job scheduling the movement of files for a disk backup.  

I want a monitoring server to alert me if there aren't any recent files in that path, so I'll get an e-mail that the backups aren't running.

I wrote a script that works, but it takes forever because there are millions of files...

This works "find -type f -mtime -1"

However, it takes forever to run, and all I care about is if there is ANY file that has a modified time in the last 24 hours.  

Is there a way I can make that find command stop searching after it finds the first result?  Cause if there are any results then I know the backup script is working.

---

### Post by Kissell on 2013-07-11
You know what...  I think -maxdepth will work nicely for this...  that will stop it from traversing the whole tree, yet still grab a good sample of data to verify there were some new files in the path.

find -maxdepth 5 -mtime -1 -type f

---

### Post by sudodus on 2013-07-11
I think you can use -quit with find, similar to this command.

```
find . -name "*.txt" -exec echo "Found this file: {} ; Quitting" \; -quit
```

---

