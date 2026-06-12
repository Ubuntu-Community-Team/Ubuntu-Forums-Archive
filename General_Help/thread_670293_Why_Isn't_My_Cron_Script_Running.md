---
title: "Why Isn't My Cron Script Running?"
date: 2008-01-17
forum: General Help
---

### Post by driggins on 2008-01-17
Greetings,

I have created a simple script, with some serious help from forum users, to backup my primary data drive. The name of the file is "backup.sh" and it lives in /etc/cron.daily/

Here are the full contents of backup.sh:
> #!/bin/bash
/usr/bin/rsync -r -t -v -u /media/data/Shared/ /media/backup/Shared/

This script works properly when I execute it in Terminal.

My problem seems to be that this script does not run daily. In fact, it does not appear to run at all. I'm using "ps aux" to see if this script has run. Additionally, I run the script manually and it finds newer files to backup every time.

Interestingly, when I use "ps aux" I don't see any cron information at all. Should I?

Any ideas on how to get my script to run once a day?

Thanks,
daryl

---

### Post by Borbus on 2008-01-17
Name it backup, not backup.sh.

---

### Post by driggins on 2008-01-17
Heh heh. Ok, it's renamed. If it runs tonight, I'll chalk one up to extreme ignorance. Thanks.

---

### Post by geirha on 2008-01-17
The file is executable right?

Anyway a short summary of how things are done. Anacron is the program responsible for running the scripts in /etc/cron.{daily,weekly,monthly}. Whenever it has run the scripts in one of them, it stores the date it ran them in /var/spool/anacron/ so the daily jobs for example won't be run again this day.

Anacron is started in two ways. When you boot ubuntu, anacron is run (by the init-script /etc/init.d/anacron), and runs any of the daily, weekly or monthly jobs if the timestamps in /var/spool/anacron/ indicates that this should be done. Secondly, a cron-job located at /etc/cron.d/anacron runs it every day at 7:30am.

cron must be running for the 7:30 job to run, so if ```
ps -ef | grep [c]ron
``` doesn't indicate /usr/bin/cron is running, you'll need to start it ```
sudo /etc/init.d/cron start
```

To see if anacron has been run, you can look in syslog:```
grep anacron /var/log/syslog
``` It should also display how many jobs it ran. A job in this context is all scripts in one folder. So it usually just runs one job (the daily).

---

### Post by driggins on 2008-01-17
Very helpful stuff there. Using your info, I verified that cron is running and that anacron reports a job finished at 7:36am. Having renamed the script (see above), I expect it to run on the next round of cron.daily jobs.

---

### Post by pjkoczan on 2008-01-17
Can you post the crontab entry (i.e. post the output of crontab -l)?

---

### Post by geirha on 2008-01-17
Also, to be sure the script was run, you could make it write some log messages. Something like this perhaps:
```

#!/bin/bash
echo "[`date`] rsync starting" >> /var/log/backup-script.log
# the rsync line here
ret_val=$?
echo "[`date`] rsync completed with exit status $ret_val" >> /var/log/backup-script.log

```

---

### Post by lgambett on 2008-01-17
Verify that in /etc/crontab the scripts in cron.daily are not executed, because /usr/sbin/anacron is present. Look here;

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
In this situation scripts in /etc/cron.daily are not executed.

---

### Post by geirha on 2008-01-18
> **lgambett said:**
> Verify that in /etc/crontab the scripts in cron.daily are not executed, because /usr/sbin/anacron is present. Look here;

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
In this situation scripts in /etc/cron.daily are not executed.

No, if anacron is installed, anacron will run /etc/cron.daily and friends. If it isn't installed, cron will run them. Look at /etc/cron.d/anacron

---

### Post by driggins on 2008-02-04
I added the lines suggested by gheira, ran the script manually, and found the successful output in the backup=-script log file.

Now, two days later, I've checked the log file and can see that the script has not run since I manually ran it the other day.

I ran:
> ps -ef | grep [c]ron
And here's the output:
> root      7843     1  0 Feb02 ?        00:00:00 /usr/sbin/cron

I ran:
> grep anacron /var/log/syslog
And here's the output:
> Feb  4 07:35:06 crserver anacron[8594]: Job `cron.daily' terminated
Feb  4 07:40:01 crserver anacron[8594]: Job `cron.weekly' started
Feb  4 07:40:01 crserver anacron[8769]: Updated timestamp for job `cron.weekly' to 2008-02-04
Feb  4 07:40:02 crserver anacron[8594]: Job `cron.weekly' terminated
Feb  4 07:40:02 crserver anacron[8594]: Normal exit (2 jobs run)

Does this help anyone understand why my backup script is not running automatically?

---

### Post by geirha on 2008-02-04
Hm, anacron has run, but not your script. Is there anything odd with the permissions? ```
ls -l /etc/cron.daily/
```

---

### Post by KjetilK on 2008-06-05
Did you ever find a solution to this problem? My problem is as good as identical, I even named the script backup.sh :-) All my permissions look good, 
-rwxr-xr-x 1 root root   83 2008-06-03 08:05 backup.sh
and everything else is identical to what has been described in this thread... 

If anyone got this working, I would love to hear about it.

---

### Post by chenel on 2008-06-12
"Although the directories contain periods in their names, run-parts will not accept a file name containing one and will fail silently when encountering them (bug #38022)"

-- from the Cron Howto at [https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto").

Just call it "backup", not "backup.sh".

Also, make sure you have the opening "shebang", #!/bin/bash, or it won't work.

---

