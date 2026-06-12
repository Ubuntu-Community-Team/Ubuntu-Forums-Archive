---
title: "Crontab stops script midway"
date: 2014-07-18
forum: General Help
---

### Post by dante5 on 2014-07-18
Hi.
I'm what you call a script-kiddie and running into some issues with a VERY simple backup script I did.
It works when I manually start it, but some reason, when I set a job for it, it stops midway the second operation.

It goes like this:

```

#!/bin/sh

DATE=$(date +%Y-%m-%d)


find /path/1st/log/* -not -name today.log | xargs zip -mT Backup-$DATE.zip -li -la -lf LogBackup.log /path/


scp /root/Backup-$DATE.zip server


find /path/second/log/* -not -name todaylog2.log | xargs zip -m Backup2-$DATE.zip -li -la -lf LogBackupJobs.log


scp /root/Backup2-$DATE.zip server



```

As you can notice, both operations are pretty similar. Yet, when the second one starts what I see in the log is what follows:

 adding: path/second/log/file0 (deflated 54%)
  adding: path/second/log/file1 (deflated 64%)
  adding: path/second/log/file2 (deflated 64%)
  adding: path/second/log/file3 (deflated 64%)
  adding: path/second/log/file192 (deflated 64%)

And that's it. The zip file is not created, it just ends abruptly.
The only difference is that the files in /path/second/log/ are many more than in /path/1st/file/. Around 250 daily files without "todaylog2.log".

I've tried:

1. Splitting the script into two separate files. (Same result).
2. Using tar instead of zip for the compressing. (Same result).
3. Running the script in other servers. (Same result).
4. Using a timeout on crontab. (Not sure if I did right, no way to tell).
5. Removing the options for moving and logging.

I think the problem lies in crontab. Tried googling much but can't find anything similar. Also, I'm using Ubuntu 10.04.
Any commentaries are welcome.
Thanks.

---

### Post by sedawk on 2014-07-18
Generally, when cron jobs act different from manual testing, I unset environment variables for test runs with 
env -i ./script.sh
In your case you should anyway be able to see if Backup2-$DATE.zip is created and growing and then vanishes again.
It might be that zip is started multiple times by xargs and therefore zip starts a second and third time. So if you do not
open an archive in append-mode, strange things might happen.
Traditionally, when using a pipe to communicate the list of backup files, the archive tool is "cpio", so instead of xargs+zip you only use cpio.
But as your rule for excluding files is very simple, I recommend using the exclude option coming with some archive tools. E.g. with tar this should work:

tar cvfz --exclude=todaylog2.log /path/second/log

(If you want better compression and do not care about higher CPU and memory usage, you can also try
 tar cvfj for "bz2" compression or tar cvfJ for "xz"  compression).

---

### Post by dante5 on 2014-07-22
Hi, I've taken your advice into consideration, I will update the post when done.
Thanks.

---

