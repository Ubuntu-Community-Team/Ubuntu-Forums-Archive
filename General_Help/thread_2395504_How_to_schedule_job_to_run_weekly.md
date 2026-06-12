---
title: "How to schedule job to run weekly"
date: 2018-07-02
forum: General Help
---

### Post by Ralph L on 2018-07-02
I have a TRIM job set up to run daily, but I would like to reschedule it to run weekly.  To set up my current daily TRIM job I followed the instructions on this web site:  [http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html) . Here are the steps I went through:
```
  To determine if the disk supports TRIM: (My understanding is that this will use anacron, not cron, and that it will not 
be run multiple times, if the computer was off for the scheduled time.)
       sudo hdparm -I /dev/sda | grep "TRIM supported"

Create the file /etc/cron.daily/trim with the following contents:
       #!/bin/sh
       LOG=/var/log/trim.log
       echo "*** $(date -R) ***" >> $LOG
       fstrim -va >> $LOG

Create the file /etc/logrotate.d/trim containing:
/var/log/trim.log {
       daily
       rotate 2
       notifempty
       missingok
```
If anybody can tell me how to change this to just run weekly I would appreciate it.  I would also appreciate an explanation of how to run anacron, rather than cron, so that scheduled jobs are not run multiple times if the computer was off when the job was scheduled to be run. Maybe Xubuntu just automatically runs anacron rather than cron--I don't know.

---

### Post by TheFu on 2018-07-02
Move /etc/cron.daily/trim  into /etc/cron.weekly/trim 
BTW, all scripts should use the full path to any programs they call to prevent issues.

But Ubuntu has setup weekly trim tasks automatically for at least a few years.

The pre-installed one is called fstrim on my 16.04 machine with an SSD.

---

### Post by Ralph L on 2018-07-04
TheFu:  Thank you for replying. I appreciate it.  And thanks for telling me that TRIM is automatically run.  However, a question:  Is there a log file to record that trim has run?  The reason I ask is that this site: [https://linustechtips.com/main/topic/241082-automatic-trim-support-on-ubuntu/](https://linustechtips.com/main/topic/241082-automatic-trim-support-on-ubuntu/)  (last post) says that, while the kernel supports automatic trim, ubuntu chose to disable it.  So I am not sure if trim is, or is not being run?????  Any way to find out??

Also, I still don't understand cron and anacron, and what each does.  According to this site: [https://askubuntu.com/questions/905992/deciphering-ubuntus-etc-crontab](https://askubuntu.com/questions/905992/deciphering-ubuntus-etc-crontab) anacron is used to schedule daily, weekly, and monthly jobs while cron is used to schedule hourly jobs.  If this is true, do hourly jobs just never get executed if the system is off, when execution is supposed to take place.

In addition, if the /etc/cron.daily/daily_backup is set to execute a daily backup and the system is down for 2 days, will daily_backup be executed twice (one right after the other), when the system is restarted????  I really don't want this to happen....

I am just trying to understand linux...Thanks for any insight....

---

### Post by TheFu on 2018-07-04
Dude. That techlinks article is from 2014, before SSDs were popular.  Always check that the article you are reading is for the version of software you are running. Fairly new hardware causes software to change by necessity. NVME storage is having a similar effect now.

There are usually 50-500 ways to solve any problem on Unix systems. You can use cron, anacron, a daemon process, or more complicated scripting using any language you might choose.

When just starting out on Unix, it is best to learn in a specific, directed, way, since everything builds on prior knowledge.
There are lots of ways to learn this stuff, but [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) covers things in an orderly way.  100% free, no-hassle PDF download.

For learning about each command on your system, there are manpages.

---

### Post by Tadaen_Sylvermane on 2018-07-05
Possible to direct output of fstrim to a log file. Its cronjob is in /etc/cron.weekly. edit and thats the end of it.

---

### Post by Ralph L on 2018-07-06
Guys:  Thanks for your help.  I am slowly learning things.  My bad for not finding the standard Xubuntu 18.04 weekly TRIM.  I was confused about cron, anacron, and what is done in the kernel.  I will have to study those more.

Again, thanks

---

### Post by TheFu on 2018-07-06
Nobody is born knowing this stuff.

Almost everything follows a pattern, since nobody could possibly memorize all the locations.

Xubuntu is only different from all other Ubuntu versions in the GUI. Underneath, they are all basically the same. Debian is about 98% the same. Other Linuxes are about 93% the same, other Unix systems are about 90% the same.  If there is a cron.daily, there is probably a cron.hourly, cron.weekly and a cron.monthly and maybe a cron.yearly/annual.   In Unix, look for patterns.   If you look deeper, you'll see that those directories could be named anything, but those names make sense for the intent.

If you think about, all the popular operating systems in the world today are based on Unix, except 1.  The more you stay away from the GUI, the more these are similar.

Nobody can know everything.  I figure I know about 10% of Linux after 25 yrs of learning.

---

