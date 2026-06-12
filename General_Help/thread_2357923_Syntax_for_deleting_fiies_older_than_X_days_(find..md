---
title: "Syntax for deleting fiies older than X days? (find...+mtime..)"
date: 2017-04-07
forum: General Help
---

### Post by mcman56 on 2017-04-07
I'm trying to delete files older than 21 days in a specific folder using cron (as root).  As I understand it, the line below should at 4:01 AM each day, delete all files older than 21 days in the directory "find /home/foscam/FI9803P_C4D655404959/record".  It does not work and does not even delete files that are much older.  Is my syntax wrong?  Is there a log I could look at to see what really happens when the command is executed?

01 04 * * * find /home/foscam/FI9803P_C4D655404959/record/* -mtime +21 -exec rm -f {} \;

---

### Post by TheFu on 2017-04-07
cron doesn't have much environment. Put whatever you want into a file, a script, and run it that way.
Also, fully specify the path to any programs.
For example, use /usr/bin/find instead of 'find'

Also, the find shouldn't have a regex.
```
#!/bin/sh
DIR=/home/foscam/FI9803P_C4D655404959/record
/usr/bin/find "$DIR" -type f -mtime +21 -exec rm -f {} \; 
```

That should do it, but I didn't test it and I'm not certain about the mtime format off the top of my head. The rest is fine, but it would be better to restrict as much as possible.  I assumed you didn't want to delete any subdirs.

---

### Post by mcman56 on 2017-04-07
I ran it from terminal and it worked perfectly.  I then added it to the cron function and hopefully have the file path correct.  Thanks!!

---

### Post by papibe on 2017-04-07
I recommend using the -delete option instead of -exec rm, so that 'find' delete the files itself instead of forking a rm command.

Something like this:
```
/usr/bin/find "$DIR" -type f -mtime +21 -delete
```
Regards.

---

### Post by TheFu on 2017-04-08
Yes, **-delete** is definitely a better method.  Good catch papibe.

Should also point out that cron will send emails with the stdout and stderr output. This is automatic, but if the MTA isn't configured, it will just end up in /var/spool/mail and start filling up the disk. It is also where any errors will show up. So - you might want to see to that by either setting up the MTA to have email delivered where you will see it or redirect it to nowhere (once it is working).

OP, If this solved the issue, please mark it as [solved] using the thread tools. That helps the community.

---

### Post by mcman56 on 2017-04-08
It ran automatically last night and worked.  I had first used delete in chron but it filled up the trash folder in the file manager.  I changed to -rm to avoid that issue.  

I don't understand the MTA part.  Does chron send a file to that folder each time it is executed?  How do I keep that from filling up?  Does incrontab do the same thing?

I am sending a large number of short video files to one folder.  When I open it in the default file manager (Files), it takes minutes to list all of the files as the machine sort of grinds away.  Is there someway to fix or improve that?

Thanks

---

### Post by TheFu on 2017-04-08
MTA - Mail Transfer Agent.  Usually postfix or sendmail.  It is expected behavior for any cron tool.  In fact, if a cron tool DIDN'T I'd file a bug.  You can redirect the output to go nowhere. There are thousands of examples on the internet. "crontab redirect null" is the search.  There are problems doing that - you'll never get notified of issues/failures.  It is common to only redirect stdout to null so only stderr gets mailed. Nothing should go to stderr, unless there is an issue anyway.

Directories really shouldn't have more than 200 files or so. If you have more, expect delays and other unexpected issues - like file globbing problems from most shells. Lots of ways to split files up into subdirectories.

Feel free to manage your system however works best for you. What works best for me isn't necessarily the best for anyone else.

File manager? What's that?  I'm a server guy. We don't need no stinkin' GUI. GUIs don't work too well over a slow connection from 10K miles away.  Plus running a GUI takes away system resources better used for other things.  A GUI, that's just crazy talk.  Guess my point is made. ;)

BTW, "cron" is the normal spelling to prevent confusion.

---

