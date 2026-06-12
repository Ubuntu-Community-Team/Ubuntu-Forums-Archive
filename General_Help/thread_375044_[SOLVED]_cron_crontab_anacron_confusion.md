---
title: "[SOLVED] cron crontab anacron confusion"
date: 2007-03-03
forum: General Help
---

### Post by ridgeland on 2007-03-03
In crontab my default was:
17 *	* * *	root    run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6	* * 7	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6	1 * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly

in /etc/cron.daily I had:
cron_daily_bookmarks_backup.sh

which only copies my bookmarks as a backup:
#!/bin/bash
cp /UserHome/Firefox/bookmarks.html /Data/Linux_2006/Internet/bookmarks.html

This daily cron job never ran.
I found two things to try per forum posts
1. full path of command - so I changed cp to /bin/cp 
2. delete .sh from script name so I used cron_daily_bookmarks_backup
I also copied it to cron.hourly so it would run more frequently while I debugged it.
It ran in cron.hourly
I tried with just cp not /bin/cp and it still ran.  Crontab includes /bin in the path.
Next I changed the name back to myscript.sh  It did not run.  So delete the .sh again.
Now that I had it running in cron.hourly I copied it back to cron.daily.  It did not run.

Studying bash I learned that  "something || other"  means that if "something" is FALSE then do "other".  In crontab "run-parts --report /etc/cron.daily" will only happen when
"test -x /usr/sbin/anacron" is false.  /usr/sbin/anacron does exist.  Testing in the terminal
$ test -x /usr/sbin/anacron || echo "NADA" 
gave no echo.  changing || to && gave the echo.  
Meaning that since /usr/sbin/anacron exists the cron.daily will never happen!

So I deleted the "test -x /usr/sbin/anacron ||" part in crontab.  Now the script runs in cron.daily (similar scripts in cron.weekly work now) In /etc/crontab I changed
25 6	* * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6	* * 7	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
to just
1 9	* * *	root	run-parts --report /etc/cron.daily
7 7	* * 7	root	run-parts --report /etc/cron.weekly
Now they work.

So the confusion is:
Why the default with test -x?  I once tried crontab -l and crontab -e.  Did that change or create /usr/sbin/acnacron?  
With the revised /etc/crontab jobs run.  I tested having the PC off when the task was scheduled.  In services I had both anacron and atd on before and after the test, but the missed job was not run when the PC was restarted. How do I get missed jobs to run?
I did visit [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by WW on 2007-03-03
The test for /usr/bin/anacron ensures that cron runs the daily, weekly and monthly script *only if anacron is not installed*.  Take a look at the file /etc/anacrontab.  It is also configured to run the daily, weekly, and monthly scripts. (Well, on my system it is; I am running Ubuntu 6.06.).  So, cron is set up to run the hourly script, and anacron is set up to run the daily, weekly and monthly scripts.

This begs the question: If anacron normally takes care of the daily, weekly and monthly scripts, why did the developers also put entries in crontab for these scripts that only run if /usr/sbin/anacron does not exist?  Why would anacron not exist? (OK, if you removed the anacron package, this provides a 'failsafe' that ensures that the scripts still run, but why would you remove anacron?)

---

### Post by ridgeland on 2007-03-03
Thanks WW,
/etc/anacrontab shows the jobs are scheduled.
man anacrontab shows the format to be:
period  delay  job-identifier  command
Not as easy to pick the time as with cron.  The period 1=daily then 5=delay means anacron will run the job once per day, launching the job five minutes after the anacron daemon started, which is during the boot process.
grep -i 'anacron' /var/log/syslog
shows that anacron starts up during each boot and puts a job time-stamp somewhere to say when it last ran cron.daily etc.
maybe in my case it never ran my script because it had a "." in the name (myscript.sh).
Since I don't see where the time-stamp went I cannot manipulate it to test it.
Tomorrow morning I should see.
The way I have it now though my daily and weekly jobs will run twice.  Once from anacron and once from cron, so I'll just comment out the cron lines and rely on anacron.

I also have a 1997 PC with 192MB of RAM with Xubuntu for the OS.  There I want to make sure anacron is turned off or disabled or deleted as there are too few resources to justify having it.

---

