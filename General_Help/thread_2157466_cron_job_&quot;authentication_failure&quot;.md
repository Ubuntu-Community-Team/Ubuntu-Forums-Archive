---
title: "cron job &quot;authentication failure&quot;"
date: 2013-06-25
forum: General Help
---

### Post by NautiusMaximus on 2013-06-25
I'm having some problems getting cron jobs to run.

If I want to get a cron job to run under my own user account, using crontab -e, then that works just fine.

However, if I want to get a cron job to run as root, then it doesn't want to play. If I either put a script into the /etc/cron.daily or /etc/cron.hourly folders, or set up the job using sudo crontab -e, then the job doesn't run. I've tested this with a really simple script that just writes "hello world" to a log file, and which runs perfectly OK from a terminal.

If I check the syslog at the time the cron job should have run, I see output like this:

```
Jun 25 14:17:02 localhost CRON[29395]: Authentication failure
```

Any ideas what could be going on? I'm using Ubuntu server 12.04, and I'm also wondering if it might be related to another problem I've been having, which is described in [this thread]("http://ubuntuforums.org/showthread.php?t=2153999").

Thanks

NM

---

### Post by Vitsliputsli on 2013-06-25
Show the script, please.

---

### Post by NautiusMaximus on 2013-06-26
> **Vitsliputsli said:**
> Show the script, please.

Sure, no problem. Here it is:

```
#!/bin/sh          
DET="Plain shell script"

LOGPATH="/var/log/"

DATETIME=$(date +%Y-%m-%dT%H:%M:%S)
LOGNAME="backup-test.log"

LOGFILE="$LOGPATH$LOGNAME"

echo "$DET run at $DATETIME" >> $LOGFILE
```

As I say, it runs just fine if I run it manually from a terminal.

---

### Post by Vitsliputsli on 2013-06-27
Very strange. Have you another problems with root account? Can you login by root in terminal? Are you set up password for root?

---

### Post by SeijiSensei on 2013-06-27
Does the cron entry happen to have sudo in it?  Files like /etc/cron* or /var/spool/cron/root run with root privileges by default.  They do not need a sudo entry.

The cron entry should just be 

```
1 1 * * * /path/to/some/script
```

to run "script" every day at 1:01 am.

---

