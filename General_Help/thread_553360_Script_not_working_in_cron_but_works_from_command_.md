---
title: "Script not working in cron but works from command line"
date: 2007-09-17
forum: General Help
---

### Post by JHuizingh on 2007-09-17
I am trying to write a script to do a really simple zip backup of a directory.  I wrote a little script called backup_script.sh that looks like this:
```

#!/bin/sh

echo "Starting script at $(date)" >> /tmp/backup.log

/usr/bin/zip -9vr /home/ubuntu/test.zip /files_to_backup/

echo "Ending script at $(date)" >> /tmp/backup.log

```

When I run this from the command line, it creates the zip, and the /tmp/backup.log shows times that are 25 seconds apart like this:

```
Starting script at Mon Sep 17 16:50:23 CDT 2007
Ending script at Mon Sep 17 16:50:48 CDT 2007
```


I also try to run backup_script.sh from crontab with this line:

```
32 16 * * * /home/ubuntu/backup_script.sh
```

When it runs, in /tmp/backup.log I get something like this:

```

Starting script at Mon Sep 17 16:32:01 CDT 2007
Ending script at Mon Sep 17 16:32:01 CDT 2007

```

Note that the script starts and ends in the same second.  The zip command creates a temp file in the directory with a name like ziE5HwmU.  This file is only 7K though, when the full file should be 86MB.  The zip process seems to be getting interrupted for some reason.  Does anybody have an idea why?

---

### Post by yabbadabbadont on 2007-09-17
> **JHuizingh said:**
> ```
32 16 * * * /home/ubuntu/backup_script.sh
```

Try redirecting the output of the script to its own logfile in /tmp to see if any errors will show up.

```
32 16 * * * /home/ubuntu/backup_script.sh > /tmp/backup_errors.log
```

---

### Post by dcstar on 2007-09-18
> **JHuizingh said:**
> I am trying to write a script to do a really simple zip backup of a directory.  I wrote a little script called backup_script.sh that looks like this:
.......
Note that the script starts and ends in the same second.  The zip command creates a temp file in the directory with a name like ziE5HwmU.  This file is only 7K though, when the full file should be 86MB.  The zip process seems to be getting interrupted for some reason.  Does anybody have an idea why?

Are you **sure** that the account you run the Cron job under has permissions to write to the directory that the script uses?

---

### Post by JHuizingh on 2007-09-18
Thank you both for the responses.

dcstar:  I am fairly sure that the user has access to write to the directory.  I run 'crontab -e' as the user ubuntu.  The backup script, for now, is writing to /home/ubuntu.  It should have access to write to that directory right?  It does create a temporary file as it is writing.

yabbadabbadont:  You're on to something here.  I tried putting the output of the cron job to /tmp/backup_errors.log:

If the target file of the zip command existed, then /tmp/backup_errors.log was created by the cron job, but it was empty.

If the target file of the zip command did not exists, then /tmp/backup_errors.log was created, and it has a number of lines like this:

```
  adding: /files_to_backup/file_1   (in=74649) (out=66584) (deflated 11%)
  adding: /files_to_backup/file_2   (in=995) (out=458) (deflated 54%)
  adding: /files_to_backup/file_3   (in=618) (out=300) (deflated 51%)
  adding: /files_to_backup/file_4
```

Note, it ends exactly as you see here.  There are many more files, but the zip command seems to end prematurely.  What can I do to figure out zip is ending prematurely?

---

### Post by JHuizingh on 2007-09-18
I figured out the issue.  I found another thread that said cron has an issue with commands that put out too much to standard out.  When I redirected that to /dev/null, it worked!

> /dev/null 2>&1

---

