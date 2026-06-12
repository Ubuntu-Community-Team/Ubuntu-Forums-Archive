---
title: "Cron Job"
date: 2015-09-24
forum: General Help
---

### Post by Ritzie on 2015-09-24
My cron job looks like this in Ubuntu 14.04:

00 2 * * 1-5 /home/ritzie/dm_hibernate.sh
00 2 * * 6,0 /home/ritzie/dm_hibernate.sh

So during the week it comes on at 5pm and shuts down at 2AM. On the weekends it comes on at 12pm and shuts down at 2pm. However it doesn't shut down every day. It seems to shut down every other day. I cannot figure it out.

---

### Post by tgalati4 on 2015-09-24
Welcome to the forums.

How do you wake your computer at 5 pm?  What is in your dm_hibernate.sh script?

Since this is a system-wide hibernate, try putting your scripts in /etc/crontab.  Make sure you add "root" in the 6th field.  Creating a User crontab:

```
crontab -l
```

means that certain functions that would affect other users on your system (like shutting down, hibernating, etc) are restricted.

I'm not sure zero is recognized.  Sunday is Day 7--so your 6,0 should be 6,7.

Also some system cronjobs run at odd hours (like 3 am) and will possibly wake your system to perform them.  So you either have to disable them or modify the time when they happen.

Finally, uncheck the setting "Allow USB devices to Wake" in your BIOS.  If you have a cat, they love to get on the internet in the middle of the night and watch cat videos.

---

### Post by nerdtron on 2015-09-25
Not sure about your crontab behavior but 0 and 7 will be recognized as Sunday. And also, crontab can recognize entries in days but it won't be possible to put ranges on that mode:

```


       Names  can  also be used for the 'month' and 'day of week' fields.  Use
       the first three letters of the particular day or month (case  does  not
       matter).  Ranges or lists of names are not allowed.

       The time and date fields are:

              field          allowed values
              -----          --------------
              minute         0-59
              hour           0-23
              day of month   1-31
              month          1-12 (or names, see below)
              day of week    0-7 (0 or 7 is Sunday, or use names)

       A  field  may  contain  an  asterisk  (*),  which  always  stands   for
       "first-last".



```

---

### Post by Ritzie on 2015-09-25
> **tgalati4 said:**
> Welcome to the forums.

How do you wake your computer at 5 pm?  What is in your dm_hibernate.sh script?

Since this is a system-wide hibernate, try putting your scripts in /etc/crontab.  Make sure you add "root" in the 6th field.  Creating a User crontab:

```
crontab -l
```

means that certain functions that would affect other users on your system (like shutting down, hibernating, etc) are restricted.

I'm not sure zero is recognized.  Sunday is Day 7--so your 6,0 should be 6,7.

Also some system cronjobs run at odd hours (like 3 am) and will possibly wake your system to perform them.  So you either have to disable them or modify the time when they happen.

Finally, uncheck the setting "Allow USB devices to Wake" in your BIOS.  If you have a cat, they love to get on the internet in the middle of the night and watch cat videos.

HAHAHHAHAH

I have a script on my router that wakes up the PC. Here is what is in my dm_script. 

#!/bin/sh

#pm-hibernate must be run as root.  but sudo requires a password.
#so, i edited /etc/sudoers so that sudo does no require a password when 
#pm-hibernate is being called.
#added the following line: "ritzie ALL = NOPASSWD: /usr/sbin/pm-hibernate"

sudo pm-hibernate

This is whats in my /etc/crontab

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

I've disabled everything I possibly can in the bios that would wake it up. I'll make the change for Sunday and put the cron job under etc. Thanks for all your help.

---

### Post by tgalati4 on 2015-09-25
I was wondering how you got around sudo privileges by running a User cronjob.  That's a clever trick.  But try putting *pm-hibernate* in /etc/crontab and see if your system sleeps consistently.

---

### Post by Ritzie on 2015-09-25
> **tgalati4 said:**
> I was wondering how you got around sudo privileges by running a User cronjob.  That's a clever trick.  But try putting *pm-hibernate* in /etc/crontab and see if your system sleeps consistently.

:) I'll make the change today. I'll hit back probably on Monday or Tuesday let you kow how it worked.

---

### Post by Ritzie on 2015-09-28
Well now I cannot get it to hibernate at all. Three days straight it stayed on. I can manually hibernate it but cannot get the script to run. Maybe I should start from scratch. What is the best way to do this? My brained is completely fried from working onthis.

---

### Post by tgalati4 on 2015-09-28
There should be log files in /var/log that you can examine.  Look for pm-suspend.log and pm-powersave.log.  Also look at auth.log since cronjob failures will show up there.

---

### Post by Ritzie on 2015-09-29
I attached the pm hibernate log.

---

### Post by tgalati4 on 2015-09-29
What was in auth.log?  That is the authorization log file for root activities, such as system cronjobs.  I didn't see any errors in your pm-suspend log files.  Everything looks good.  I presume these were from manually running *pm-suspend* or *pm-hibernate*?

---

