---
title: "Can't create cron jobs"
date: 2013-12-21
forum: General Help
---

### Post by psyq-klay on 2013-12-21
I'm having an utterly baffling problem with crontab. Been going around in circles on the forum and google trying to find a solution

Every time I run "crontab -l" the result is "no crontab for user" or "no crontab for root". Ok, np, so I run "crontab -e" and setup a simple @reboot for my backlight brightness. Once I reboot it goes back to "no crontab for user" again. Nothing seems to save. Tried gnome-schedule too with similar results. This is a fresh install of 13.10

Spent 3 hours on this. Gonna lose it. Help!

---

### Post by claracc on 2013-12-21
Have you tried to read the manual entry for crontab?

In a xterm, you can run:```
man crontab
```

It explains you how to use "crontab" command, specifically, man says:
```
 If the /etc/cron.allow file exists, then you must be listed  (one  user
       per  line)  therein in order to be allowed to use this command.  If the
       /etc/cron.allow file does not exist but the  /etc/cron.deny  file  does
       exist,  then you must not be listed in the /etc/cron.deny file in order
       to use this command.

       If neither of these files exists, then depending on site-dependent con&#8208;
       figuration  parameters, only the super user will be allowed to use this
       command, or all users will be able to use this command.

       If both files exist then /etc/cron.allow takes precedence. Which  means
       that  /etc/cron.deny  is not considered and your user must be listed in
       /etc/cron.allow in order to be able to use the crontab.

       Regardless of the existance of any of these files, the root administra&#8208;
       tive  user  is  always allowed to setup a crontab.  For standard Debian
       systems, all users may use this command.

```

---

### Post by psyq-klay on 2013-12-21
Yup, I read that. Neither files exists in /etc so it sounds like that means anyone can use it without restriction.

---

### Post by psyq-klay on 2013-12-21
I stared up logging and it looks like my problem is here:

anacron[1913]: Can't chdir to /var/spool/anacron: No such file or directory

Kinda surprised to have issues in this area with a fresh install. anacron won't start without creating /var/spool/anacron and it does not persist after a reboot. Stumped again.

---

