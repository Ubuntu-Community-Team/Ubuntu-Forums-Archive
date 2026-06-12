---
title: "Automatically deleting files older than two days?"
date: 2007-07-20
forum: General Help
---

### Post by jrattner on 2007-07-20
How would I set up a Cron job to automatically delete files in a certain directory which are older than two days?

---

### Post by yabbadabbadont on 2007-07-20
If you just want to clear out files that were last modified more than 2 days ago then you can do it with a command that looks something like this:
```
find /path/to/directory -type f -daystart -mtime +2 -exec rm -f {} \;
```
You should read the "find" manual page for details on the options I have used.  ("man find" in a terminal window)

---

### Post by xarmian on 2007-07-20
> **jrattner said:**
> How would I set up a Cron job to automatically delete files in a certain directory which are older than two days?

The easiest way I know of is to use find.. and it's very customizable.. for example, you can delete all files last modified after a certain date, after a number of days, etc.  Or you can do the same but based on the last status change, access time, or even the last modification date of another file.

For example, to FIND all files in /home/dave/logs (and all subfolders as well) which were last modified over two days ago (48 hours), you would use:

find /home/dave/logs -type f -mtime +2

If you add the -exec flag you can then execute something, such as rm'ing (deleting) the files, so the following command will delete all files last modified more than 48 hours ago in the /home/dave/logs folder:

find /home/dave/logs -type f -mtime +2 -exec rm -f {} \;

There are a lot of other flags that can be used with find, making it a very powerful tool, but **be careful** because the above will NOT be forgiving and will permanently delete the files right away.

-Dave

EDIT: I got beat to the punch.. :-P

Just a note, the -daystart flag mentioned above by yabbadabbadont measures the last modification time based on the start of the day (midnight).  If you do not use -daystart it measures it based on the time that the command is executed (such as the time the cronjob is scheduled to run)

---

### Post by jrattner on 2007-07-20
Thanks guys

---

