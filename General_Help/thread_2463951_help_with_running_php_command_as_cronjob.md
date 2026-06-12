---
title: "help with running php command as cronjob"
date: 2021-06-21
forum: General Help
---

### Post by linuxpc4me on 2021-06-21
Hello!  This my first post.  I hope it is in the right place.

UPDATED Post as I did not include the cronjob:

45 7-16 * * * /usr/bin/php /var/www/html/modules/mod_sv_reminders_sms/reminders_cron_sms.php >> /var/log/apptsms.log 2>&1

As that failed, I removed the output at the end to read:

45 7-16 * * * /usr/bin/php /var/www/html/modules/mod_sv_reminders_sms/reminders_cron_sms.php 

This runs the cronjob hourly starting at 7:45 am and ending at 4:45 PM

It is designed to harvest all appointments scheduled during the day, sending a reminder TXT for all appointments within that hour timeframe

Apologies for the omission of that information....

I have a php script that should work via cronjob.  When I search for it in syslog, it shows up, and if I'm looking correctly, it did not error:
Jun 21 14:45:01 RCE1ApptPro CRON[69048]: (stevek) CMD (/usr/bin/php /var/www/html/modules/mod_sv_reminders_sms/reminders_cron_sms.php)
Jun 21 15:00:01 RCE1ApptPro CRON[69581]: (root) CMD (/usr/bin/php /var/www/html/modules/mod_sv_reminders_sms/reminders_cron_sms.php)
Jun 21 15:17:01 RCE1ApptPro CRON[69858]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 21 15:30:01 RCE1ApptPro CRON[70113]: (root) CMD ([ -x /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
Jun 21 15:35:04 RCE1ApptPro systemd[1]: Started Run anacron jobs.
Jun 21 15:35:05 RCE1ApptPro anacron[70197]: Anacron 2.3 started on 2021-06-21
Jun 21 15:35:05 RCE1ApptPro anacron[70197]: Normal exit (0 jobs run)
Jun 21 15:35:05 RCE1ApptPro systemd[1]: anacron.service: Succeeded.

However, the task it is suppose to do does not happen.  I think it is a permission thing but am a loss ( the execution path is owned by me, not apache)
Yes, it is listed twice, once in my crontab and once in root to see if one would work, neither do

Can someone help explain what this excerp from syslog means, and, some starting point to get the cronjob to work?

Thanks in advance!

---

### Post by scorp123 on 2021-06-21
Please post the job? Log output alone doesn't tell us much...

---

### Post by TheFu on 2021-06-21
Most php tasks are expected to be run as the userid that runs apache/nginx processes.  On Ubuntu, that would www-data almost always.
Cron doesn't have a complete environment like an interactive desktop. That means most environment variables are NOT set. If you want any set, then your script needs to do that.

So ... to run a task periodically, using the www-data userid, I do it this way:

First, we have to edit the www-data crontab. Not your personal userid or root's crontab:
```
sudo -e -u www-data
```

then we add the entry in the correct format:
```
# m h  dom mon dow   command
3  */2  *  *  * /usr/bin/nextcloud-news-updater --threads 2 --mode singlerun /var/www/html/nextcloud >> /dev/null  2>&1

```
My example runs the nextcloud-news-updater every even hour at 3 minutes after every day. This runs as the www-data userid.

You would use something like this:
```
15 * * * * /usr/bin/php /var/www/html/modules/mod_sv_reminders_sms/reminders_cron_sms.php >> /dev/null  2>&1
```

If the script assumes a PWD, it won't work.  Cron doesn't set the pwd/cwd.  All scripts should run from any directory on the system exactly the same.  Any files to be read or written must be able to be accessed by the www-data userid.  The php.ini file used will probably matter too. Different versions of php can be installed on the same system, which can leave php scripts with a split brain problem.  Ensure the correct php.ini is being used however that is accomplished in php.

Running php scripts as root is dangerous. I wouldn't do it.

If you don't want to use crontab -e, which writes crontabs to specific userid files in /var/spool/cron/crontabs/, then you can use the /etc/crontab file and specify the userid to be used inside it.  /etc/crontab uses a slightly different format, but there should be 3+ examples to follow already in there.

If you are still having  issues, check the environment between the interactive session that works and the cron environment that doesn't 
```
env > /tmp/interactive-env
```
or put that into the different crontab -e versions as  
```
/usr/bin/env > /tmp/$USER-env
```
Next use any file comparison tool to compare the output files. I like **meld**, which is probably the best comparison tool on any platform.

---

### Post by dragonfly41 on 2021-06-21
A parallel universe ...

[https://www.phphelp.com/t/insert-date-time-in-php-cronjob/33621](https://www.phphelp.com/t/insert-date-time-in-php-cronjob/33621)

Can you not launch php dev server instead (php -S localhost:8000) and then append result to your log file.

---

### Post by linuxpc4me on 2021-06-21
scorp123 --- I updates my post to include the missing data.   Thanks for looking at it

---

### Post by linuxpc4me on 2021-06-21
TheFu,  Thank you so much for your post... I did update mine to include the actual cronjob.

---

### Post by TheFu on 2021-06-21
> **linuxpc4me said:**
> TheFu,  Thank you so much for your post... I did update mine to include the actual cronjob.

It would really help us if terminal output and text files were wrapped in code-tags here.  That's the Adv Reply (#) button or you can do it manually.  Not a big deal with these since they aren't column pretty, but there's something about a mono-spaced **code **text block that helps people used to terminal output jump directly to the important places.  No need to ever touch the fonts, the tag-wrappers do what's needed.

If it is a permission issue, then there isn't really any shortcut besides sitting down for 45 minutes, working through a Unix permissions tutorial for 15 minutes, then spending the next 30 minutes in a new /tmp/foo directory with 3 terminals, 3 different userids and 2 groups, then mix and match every possible group, user and permission possible until the elegance "clicks" in your head.  45 minutes now will save you hours, days, weeks, months of frustration AND probably being hacked.  Plus, this permissions model is used by every popular OS on the planet today except 1.  All the others use it.  All of them.

BTW, I don't see anything material in the updated post.  Look inside that log file for an error. See what is says and fix it.

---

### Post by scorp123 on 2021-06-22
> **linuxpc4me said:**
>  However, the task it is suppose to do does not happen.  I think it is a permission thing ...

What happens if you execute the job's content outside of "cron" e.g. in an interactive shell? Does it work as intended there and really do what it was supposed to?

---

### Post by TheFu on 2021-06-22
Does the php script set different return codes based on different failures?  If it doesn't set a non-zero return code, then the parent process will not consider it a failure.  The programmer has that responsibility and should test the RC from every call.

---

### Post by SeijiSensei on 2021-06-22
I use the normal hash-bang method.

```

#!/usr/bin/php

<?php

php code here

?>

```

I put this into a file and mark it executable. Then you just need to call the script in a crontab.

---

