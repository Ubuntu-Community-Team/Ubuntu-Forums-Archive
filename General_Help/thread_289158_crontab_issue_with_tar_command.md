---
title: "crontab issue with tar command"
date: 2006-10-30
forum: General Help
---

### Post by digital-IQ on 2006-10-30
I am having an issue with a tar command in crontab.  The tar command is in a script that can be executed from the command line an it runs properly.  When the same sript is called from crontab it creates the archive but the size is only 30 MB when it shoudl be 3.2 GB.  The tar file is also corrupted.

Script:
```
# backup script for file-server
# 
# 

#backup shared folder and store in archive folder
tar -zcvpf /home/archive/shared_`date +%Y-%m-%d`.tar.gz /home/shared
```

I have even tried putting the tar command in crontab inplace of the script with the same result.  I have tried putting it in the system crontab as well as root crontab.  The same results are seen each time.

I am sure I have overlooked something rather simple, but I haven't found anything in any other posts that help with this issue.

Thanks

---

### Post by chippy99 on 2006-10-30
I think cron wants full path names to files so you need to give the full path to the tar program. Type whereis tar to find it, I have not got access to a Ubuntu box at the moment but on suse its /bin/tar.

---

### Post by bsussman on 2006-10-30
> **digital-IQ said:**
> 
```
# backup script for file-server
# 
# 

#backup shared folder and store in archive folder
tar -zcvpf /home/archive/shared_`date +%Y-%m-%d`.tar.gz /home/shared
```

Suggest you direct tar's output and error out to a logfile so you can see what it is doing.  You might also want to save it's returncode.

```
tar  -zcvpf /home/archive/shared_`date +%Y-%m-%d`.tar.gz /home/shared > logfile 2>&1
```a start log message and end log message might be nice too.

---

### Post by digital-IQ on 2006-10-30
Thanks chippy99.  Works fine now.

---

### Post by shane2peru on 2006-12-05
> **bsussman said:**
> Suggest you direct tar's output and error out to a logfile so you can see what it is doing.  You might also want to save it's returncode.

```
tar  -zcvpf /home/archive/shared_`date +%Y-%m-%d`.tar.gz /home/shared > logfile 2>&1
```a start log message and end log message might be nice too.

Where exactly will this log file be located and named?  This thread is basically the same issue I am having.  Thanks.

Shane

PS  - Also I have never written a script, I basically copied the above format, does it need to have a special extension?  I just called it .backupscript  with no extension, and hidden so I won't accidentally erase it while cleaning up my /home directory.

---

### Post by shane2peru on 2006-12-06
Ok, I have managed to get it all working correctly.  I still don't have a log file.  It would be nice to know how to get it to leave me a log somewhere, if  any kind soul stumbles across this thread, and just happens to know how to get the output of this thing printed to a log file, and knows where to find the log file afterward, I would be thankful.  Thanks

Shane

---

### Post by SyvanX on 2006-12-06
bsussman's code should work for you, just replace *logfile* with the absolute path to the directory you want the file stored in. ex: ~/log/tar_cron.log, just make sure the directory exists and is writeable.

```
tar  -zcvpf /home/archive/shared_`date +%Y-%m-%d`.tar.gz /home/shared > logfile 2>&1

```

---

### Post by shane2peru on 2006-12-08
> **SyvanX said:**
> bsussman's code should work for you, just replace *logfile* with the absolute path to the directory you want the file stored in. ex: ~/log/tar_cron.log, just make sure the directory exists and is writeable.

```
tar  -zcvpf /home/archive/shared_`date +%Y-%m-%d`.tar.gz /home/shared > logfile 2>&1

```
Thanks!  worked like a charm.

Shane

---

