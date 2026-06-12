---
title: "crontab @reboot fails to run"
date: 2021-05-17
forum: General Help
---

### Post by pcla56 on 2021-05-17
Hi Team,

I am running 20.04.2 server

sudo crontab -u www-data -l:

# update gn with latest additions and deletions
0 * * * * /usr/bin/php7.4 /var/www/html/gnb/index.php cron index junk
# clean up sessions older than 2hrs
5 1,3,5,7,9,11,13,15,17,19,21,23 * * * find /var/www/html/sessions/*/* -mmin +120 -exec rm {} \;

cat /etc/cron.d/start_on_reboot:

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
@reboot www-data /usr/bin/php7.4 /var/www/html/gnb/index.php cron index junk

I can see following syslog entries:

May 17 19:53:01 ikserver2 cron[544]: (*system*start_on_reboot) RELOAD (/etc/cron.d/start_on_reboot)
May 17 19:56:39 ikserver2 cron[581]: (CRON) INFO (pidfile fd = 3)
May 17 19:56:39 ikserver2 cron[581]: (CRON) INFO (Running @reboot jobs)
May 17 19:56:40 ikserver2 CRON[736]: (www-data) CMD (/usr/bin/php7.4 /var/www/html/gnb/index.php cron index junk)

BUT nothing runs! I would expect to see:

www-data    1315    1312  0 20:00 ?        00:00:00 /bin/sh -c /usr/bin/php7.4 /var/www/html/gnb/index.php cron index junk
www-data    1316    1315  0 20:00 ?        00:00:00 /usr/bin/php7.4 /var/www/html/gnb/index.php cron index junk


I originally added '@reboot /usr/bin/php7.4 /var/www/html/gnb/index.php cron index junk' into www-data's crontab but still nothing.

Yes, I have read the manual.
Yes, I have read extensive advice on the quirks of cron online.

This is rediculously hard. What is going on?

Please someone put me out of my misery!

---

### Post by scorp123 on 2021-05-17
Why not a **systemd.service** and define a "ExecStop" condition (e.g. what needs to happen when the service gets shut down; this is analoguous to the old "init.d" kill scripts ...)?  That's how I'd do that, not via "cron" ...

---

### Post by Tadaen_Sylvermane on 2021-05-17
I'm kind of curious to see this script. I just did a man page search for cron, index, junk in the php page and found nothing. I'm not sure you are doing what you think you are doing? If the script isn't right it will show it run but it will have no effect.

For the record I'm not experienced in php.

---

### Post by pcla56 on 2021-05-18
Thanks for suggestions. I will have a look at the service options but still feel cron functions should do what I want?
The command is actually running a codeigniter controller and works fine once system is up and running ie the normal cron hourly invocation works fine. It’s just trying to get it started in case of a reboot that is proving so difficult to solve. I did wonder if it was something to do with the startup sequence of apache and MySQL. If so how can I delay the reboot cron job

---

### Post by dinkidonk on 2021-05-18
The common issue with cron is that there is no environment available so if any of the commands rely on information from the env, they will fail. You could try to debug you issue by creating a shell script that runs the wanted command and when that shell script works as expected, make cron run the shell script instead of the actual command.

---

### Post by scorp123 on 2021-05-19
> **pcla56 said:**
>  It’s just trying to get it started in case of a reboot that is proving so difficult to solve.  Starting + stopping stuff is what systemd and its services are for and I'd use that. The hourly stuff is fine with cron.

---

### Post by TheFu on 2021-05-19
Nothing in /etc/cron.d/ gets run automatically. It is a directory just to hold scripts. Those scripts need to be invoked from somewhere else controlled by cron or anacron.

For reboot scripts, I'd add a line to /etc/crontab or the root's crontab (sudo crontab -e).  Either of those will work. BTW, the userid to be used field is required for /etc/crontab, but assumed for crontabs in /var/spool/cron/crontabs/ based on the userid.

'find' has  -delete,  100x faster than -exec rm .... 
I'd use
```
 5 [COLOR="#FF0000"]*/2 [/COLOR] * * * [COLOR="#FF0000"]/usr/bin/find [/COLOR]/var/www/html/sessions/*/* [COLOR="#FF0000"]-type f [/COLOR] -mmin +120 [COLOR="#FF0000"]-delete[/COLOR]
```

---

