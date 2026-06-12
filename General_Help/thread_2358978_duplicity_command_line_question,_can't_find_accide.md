---
title: "duplicity command line question, can't find accidentally deleted file"
date: 2017-04-19
forum: General Help
---

### Post by aeronutt on 2017-04-19
I need more advanced options than deju-dup provides, so I'm investigating duplicity from the command line.
Problem is, under my test case, I can't find 'old' files I've deleted. In simple terms, if I accidentally delete a file, then do a backup, I can't seem to find the file I deleted in the backup even when I list contents using the --time switch of duplicity. Detailed example (please bare with me):

Assume the following:
1) run a full backup (eg duplicity /home <url1>)
2) delete a file (ie 'file1') in /home
3) run an incremental backup on /home (eg duplicity incr /home <url1>)

Now, nothing I do can find 'file1'.
Running 'duplicity list-current <url1>' does as it should. That is, file1 is not shown.
However, no matter what timestamp I use, eg 'duplicity list-current --time <time> <url1>', I simply can't find file1 in the archive. It always seems to show the files of the most recent backup.

(FYI, I've run 'duplicity collection-status <url1>' to get exact timestamps of backups, and used those exact times, and times before and after those exact times, to no avail)

---

### Post by aeronutt on 2017-04-19
UPDATE: Found it.
So the difficulty is with how duplicity lists times, vs what duplicity expects on the command line.
Running 'duplicity collection-status <url1>' reports using local-times. However, using those local times in the --time switch is INCORRECT. One MUST enter the time with the UTC offset added. 
E.g. 'duplicity collection-status <url1>' might report as follows:

Type of backup set:                            Time:      Num volumes:
Full         Wed Apr 19 **11:06:08 2017**                 1
Incremental         Wed Apr 19 **11:07:33 2017**                 1

BUT, when listing the files in the backups, one must enter the above times with the UTC offset added, eg:

duplicity list-current-files --time 2017-04-19T11:06:08**-04:00**

UG!!  There should be a way to run the collection-status option and report with UTC times.

---

### Post by ajgreeny on 2017-04-19
Good news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

