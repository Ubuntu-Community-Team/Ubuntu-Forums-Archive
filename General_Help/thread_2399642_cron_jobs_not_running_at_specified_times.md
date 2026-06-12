---
title: "cron jobs not running at specified times"
date: 2018-08-28
forum: General Help
---

### Post by painterengr on 2018-08-28
Initial conditions:

running Ubuntu 16.04 LTS 64bit
kernel 4.15.0-32-generic #35~16.04.1-Ubuntu SMP Fri Aug 10 21:54:34 UTC

ls -l /etc/localtime
lrwxrwxrwx 1 root root 34 Jan 21 2018 /etc/localtime -> /usr/share/zoneinfo/America/Denver

cat /etc/timezone
America/Denver

date
Fri Aug 17 17:33:42 MDT 2018

These are correct.

The group of system cron jobs, such as /etc/cron.daily/logrotate, /etc/cron.daily/00logwatch, /etc/cron.daily/dpkg, etc is supposed to run at hour 6 minute 24 every day.

It actually runs at 7:35. It seems that it is running an hour later than specified. (the few minutes between :24 and :35 is inconsequential).

Various searches all suggest setting the items I have previously listed (which are correct).

Any suggestions on fixing this?

regards
oldunixguy

---

### Post by TheFu on 2018-08-29
Please prove your statements around the proposed time to run.
/etc/crontab controls is and contains here:
```
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
```

So my /etc/cron.daily/ scripts all run at 6:25am, if the machine is on.  I didn't power on until 6:42am today, so that is when they ran today.

Weekly and monthly jobs run later.

---

### Post by painterengr on 2018-08-29
here is /etc/crontab. I have never edited this file. In webmin for the job group I did set the time to 06:24 daily

17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
24 6 * * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

logwatch which is part of the cron block of jobs shows every day it runs at 7:35 :
 ################### Logwatch 7.4.2 (02/27/16) #################### 
        Processing Initiated: Wed Aug 29 07:35:03 2018
        Date Range Processed: yesterday
                              ( 2018-Aug-28 )
                              Period is day.
        Detail Level of Output: 0
        Type of Output/Format: mail / text
        Logfiles for Host: PEI-Server


webmin's cron screen shot of the top level is attached. Followed by the time for the block in question that runs actually at 7:35

webmin shows this block is supposed to run at 06:24
This appears to correspond with the 24 6 entry in /etc/crontab

thanks
oldunixguy

---

### Post by TheFu on 2018-08-29
Can't help with webmin support. Sorry. Maybe ask for help on the webmin support forum?

I use logwatch too. 

On my laptop (this system), logwatch ran at 8:53a this morning because the computer wasn't powered at the specific time it was supposed to run, so anacron uses a random delay.   Could that be what you are experiencing?

Also, there's an anacrontab file that the manpage says overrides the crontab.  Anacron isn't good at doing things at specific times. It works on a daily scale, not hourly or by the minute according to the manpage.  If you need a job to run at a specific time and only that time, don't use anacron.  ```

       For each job, Anacron checks whether this job has been executed in  the
       last  n  days,  where  n is the period specified for that job.  If not,
       Anacron runs the job's shell command, after waiting for the  number  of
       minutes specified as the delay parameter.
```

---

### Post by painterengr on 2018-08-29
I understand.... but.

I have a number of other systems that are setup in the same way and they fire off at the prescribed times.
And this is a server that is running 24x7.
And this logwatch actually runs every day at 07:35 instead of the prescribed 06:24.

I will keep searching for what is making this go at the wrong time.

thanks
oldunixguy

---

### Post by TheFu on 2018-08-29
might try cleaning out the anacron timestamp files. Might help?

---

### Post by painterengr on 2018-08-29
will do
thanks!
oldunixguy

---

### Post by TheFu on 2018-08-30
I was reading the READM.gz file for anacron:```

   Anacron is not an attempt to make cron redundant.  It cannot
currently be used to schedule commands at intervals smaller than days.
It also does not guarantee that the commands will be executed at any
specific day or hour.
...
2. Decide which of these jobs should be controlled by Anacron.
   Remember that Anacron does not guarantee execution at any specific
   day of the month, day of the week, or time of day.  Jobs for which
   the timing is critical should probably not be controlled by
   Anacron.
```

So if you want more control, move the jobs from anacron over to cron.

---

