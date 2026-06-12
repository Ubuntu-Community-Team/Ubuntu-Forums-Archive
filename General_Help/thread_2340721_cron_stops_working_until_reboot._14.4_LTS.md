---
title: "cron stops working until reboot. 14.4 LTS"
date: 2016-10-21
forum: General Help
---

### Post by NotQuiteSU on 2016-10-21
I can't understand why, but my cronjobs stop working at random intevals until I reboot, update cron, or restart the service
```

$sudo service cron status
cron start/running, process 1417
```

My Cron list
```
# m h  dom mon dow   command
20 8 * * * /home/sysadmin/scripts/script.sh 2>&1 >> /home/sysadmin/errors.txt
0 * * * * /home/sysadmin/scripts/websearch.sh 2>&1 >> /home/sysadmin/errors.txt
06 15 * * *  echo "Just testing if crond sends email"
12 10 * * * /home/sysadmin/scripts/croncheck.sh

```

I have a couple scripts which send emails.



Syslog from 2 different times. Successful and failures. I am using msmtp for email, rather than mail, since I'm relaying rather than running a mail server. 
> 

 
Oct 20 13:05:12 MyServerName console-kit-daemon[2310]: WARNING: Failed to add monitor on '/dev/pts/0': No space left on device
Oct 20 13:07:46 MyServerName sudo: pam_ecryptfs: pam_sm_authenticate: /home/sysadmin is already mounted
Oct 20 13:17:01 MyServerName CRON[3143]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 20 14:00:01 MyServerName CRON[4793]: (sysadmin) CMD (/home/sysadmin/scripts/websearch.sh 2>&1 >> /home/sysadmin/errors.txt)
Oct 20 14:00:06 MyServerName msmtp: host=smtp.gmail.com tls=on auth=on user=MyEmailAddress from=MyEmailAddress@gmail.com recipients=MyEmailAddress@gmail.com mailsize=728 smtpstatus=250 smtpmsg='250 2.0.0 OK 1476986406 n128sm11738271qka.49 - gsmtp' exitcode=EX_OK
Oct 20 14:17:01 MyServerName CRON[5720]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 20 14:41:47 MyServerName kernel: [ 5976.516793] perf interrupt took too long (2901 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Oct 20 15:00:01 MyServerName CRON[7332]: (sysadmin) CMD (/home/sysadmin/scripts/websearch.sh 2>&1 >> /home/sysadmin/errors.txt)
Oct 20 15:00:05 MyServerName msmtp: host=smtp.gmail.com tls=on auth=on user=MyEmailAddress from=MyEmailAddress@gmail.com recipients=MyEmailAddress@gmail.com mailsize=565 smtpstatus=250 smtpmsg='250 2.0.0 OK 1476990005 j2sm24177924qtb.46 - gsmtp' exitcode=EX_OK
Oct 20 15:06:01 MyServerName CRON[7892]: (sysadmin) CMD (echo "Just testing if crond sends email")
Oct 20 15:06:03 MyServerName msmtp: host=smtp.gmail.com tls=on auth=on user=MyEmailAddress from=MyEmailAddress@gmail.com recipients=MyEmailAddress@gmail.com mailsize=383 smtpstatus=250 smtpmsg='250 2.0.0 OK 1476990362 f189sm19939911qkb.32 - gsmtp' exitcode=EX_OK
Oct 20 15:17:01 MyServerName CRON[8302]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 20 16:00:01 MyServerName CRON[9912]: (sysadmin) CMD (/home/sysadmin/scripts/websearch.sh 2>&1 >> /home/sysadmin/errors.txt)
Oct 20 16:17:01 MyServerName CRON[10818]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 20 16:50:01 MyServerName CRON[12060]: (sysadmin) CMD (/home/sysadmin/scripts/croncheck.sh)
Oct 20 17:00:01 MyServerName CRON[12408]: (sysadmin) CMD (/home/sysadmin/scripts/websearch.sh 2>&1 >> /home/sysadmin/errors.txt)
Oct 20 17:15:59 MyServerName console-kit-daemon[2310]: message repeated 975 times: [ WARNING: Failed to add monitor on '/dev/pts/0': No space left on device]


 
Oct 21 09:00:01 MyServerName CRON[16044]: (sysadmin) MAIL (mailed 1 byte of output; but got status 0x004e, #012)
Oct 21 09:17:01 MyServerName CRON[16668]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 21 10:00:01 MyServerName CRON[18233]: (sysadmin) CMD (/home/sysadmin/scripts/websearch.sh 2>&1 >> /home/sysadmin/errors.txt)
Oct 21 10:00:01 MyServerName CRON[18231]: (sysadmin) MAIL (mailed 1 byte of output; but got status 0x004e, #012)
Oct 21 10:04:54 MyServerName sudo: pam_ecryptfs: pam_sm_authenticate: /home/sysadmin is already mounted
Oct 21 10:05:59 MyServerName console-kit-daemon[2310]: WARNING: Failed to add monitor on '/dev/pts/0': No space left on device
Oct 21 10:09:44 MyServerName crontab[18790]: (sysadmin) LIST (sysadmin)
Oct 21 10:10:00 MyServerName crontab[18827]: (sysadmin) BEGIN EDIT (sysadmin)
Oct 21 10:10:15 MyServerName crontab[18827]: (sysadmin) REPLACE (sysadmin)
Oct 21 10:10:15 MyServerName crontab[18827]: (sysadmin) END EDIT (sysadmin)
Oct 21 10:10:17 MyServerName crontab[18839]: (sysadmin) BEGIN EDIT (sysadmin)
Oct 21 10:10:24 MyServerName crontab[18839]: (sysadmin) REPLACE (sysadmin)
Oct 21 10:10:24 MyServerName crontab[18839]: (sysadmin) END EDIT (sysadmin)
Oct 21 10:10:25 MyServerName crontab[18850]: (sysadmin) LIST (sysadmin)
Oct 21 10:11:01 MyServerName cron[1417]: (sysadmin) RELOAD (crontabs/sysadmin)
Oct 21 10:12:01 MyServerName CRON[18922]: (sysadmin) CMD (/home/sysadmin/scripts/croncheck.sh)



---

### Post by SeijiSensei on 2016-10-21
This looks to be the culprit
> Oct 20 17:15:59 MyServerName console-kit-daemon[2310]: message repeated 975 times: [ WARNING: Failed to add monitor on '/dev/pts/0': No space left on device]
but I have no idea why it would have no space left.  /dev/pts exists only in system memory.  I assume this machine has a decent amount of memory.  For servers 1GB should be more than enough.

---

### Post by NotQuiteSU on 2016-10-21
> free -g
             total       used       free     shared    buffers     cached
Mem:            15         15          0          0          0         12
-/+ buffers/cache:          2         13
Swap:            0          0          0


This may be the cause - 

[https://bofhdiaries.wordpress.com/2012/11/29/linux-crashplan-ate-all-my-inotify-watches/](https://bofhdiaries.wordpress.com/2012/11/29/linux-crashplan-ate-all-my-inotify-watches/)

---

