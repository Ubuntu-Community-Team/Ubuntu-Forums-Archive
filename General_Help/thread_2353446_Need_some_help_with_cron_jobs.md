---
title: "Need some help with cron jobs"
date: 2017-02-21
forum: General Help
---

### Post by bphillips2 on 2017-02-21
I've installed a program called Time Tracker on my server for employees to clock in and out.  I'm trying to get a cron job set up to automatically send me a report on employee hours.

The [user guide]("https://www.anuko.com/time_tracker/user_guide/notifications.htm") for the program tells me to enter this for a cron job:
> # timetracker ping to execute scheduled jobs
MAILTO=""
5 * * * * root /usr/bin/php /var/www/timetracker/cron.php

However, my time tracker software installation is at [COLOR=#000000]/home/***user***/public_html/ap/.  So I've change the cron job to :
[/COLOR]> # timetracker ping to execute scheduled jobs
MAILTO=""
5 * * * * ***user*** /usr/bin/php /home/***user***/public_html/ap/timetracker/cron.php

The file permissions are:
> [COLOR=#000000]-rw-rw-r-- 1 ***user user*** 3589 Sep 10 18:20 cron.php[/COLOR]

I still can't get this to automatically send the reports. Where did I mess up?

---

### Post by Keith_Helms on 2017-02-21
Are there any log entries in /var/log/syslog that show the system tried to execute the command?

---

### Post by bphillips2 on 2017-02-22
I do not have a file /var/log/syslog, but I do have /var/log/cron.  In that file it looks like the cron job is being run every hour. I thought I had the cron job setup to run every 5 minutes ([COLOR=#000000]*5 * * * *)*[/COLOR]

> [COLOR=#000000]Feb 22 08:05:01 vps19510 CROND[32407]: (***user***) CMD (***user*** /usr/bin/php /home/***user***/public_html/ap/timetracker/cron.php)[/COLOR]

---

### Post by SeijiSensei on 2017-02-22
First, which crontab file is this?  Is it /etc/crontab, or one in /var/spool/cron created by running "crontab -e"?  If it's /etc/crontab, then the syntax you provided is correct.  If it's "user's" own crontab, then there shouldn't be a "user" field in this command:
> ```

# timetracker ping to execute scheduled jobs
MAILTO=""
5 * * * * user /usr/bin/php /home/user/public_html/ap/timetracker/cron.php 
```
First, make sure that you can run the command as "user" by entering the complete command above from the terminal prompt when logged in as "user."

Next, putting a five in the first column means the job will be run at five past every hour.  To make a job run once every five minutes use "*/5" instead.  Now jobs will run on minutes cleanly divisible by five.

---

### Post by bphillips2 on 2017-02-22
Thanks! That helped me fix it!

I am using crontab -e. I changed the syntax to the following and it worked.

> [COLOR=#000000]*/5 * * * * /usr/bin/php public_html/ap/timetracker/cron.php[/COLOR]

---

### Post by oldrocker99 on 2017-02-22
Please use the Thread Tools to mark this thread as [SOLVED] to help other users.

---

### Post by SeijiSensei on 2017-02-22
> **bphillips2 said:**
> Thanks! That helped me fix it!

I am using crontab -e. I changed the syntax to the following and it worked.

You're lucky.  Apparently it runs in the user's home directory so "public_html/ap/timetracker/cron.php" is anchored at /home/user.  I always include full paths to files in crontabs because you don't know what environment they will be running in.

---

