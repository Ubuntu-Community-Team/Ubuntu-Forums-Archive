---
title: "cron.dialy question"
date: 2013-01-07
forum: General Help
---

### Post by bandito40 on 2013-01-07
I have been fiddling with cron. If you schedule a script to run daily and your computer is off when acron has it scheduled will it run if you turn your computer on later in the day?

---

### Post by jonobr on 2013-01-09
It shouldn't , 
are you seeing something different?

Also remember that crontab -l 
is different to sudo crontab -l
You probably new that already :-)

---

### Post by Cheesehead on 2013-01-09
If the computer is turned off, then cron won't run it...but anacron likely will. That's precidely the use case that anacron (included with the default install of Ubuntu) is intended for.

Anacron runs at boot to look for missed daily/weekly/monthly cron jobs. It looks for those jobs in the normal /etc/cron.* folders.

---

### Post by bandito40 on 2013-01-11
I used anacron in the end.  This is the line I added to /etc/anacrontab.

1       5       cron.daily      php5 /var/www/mazda/backup.php


It runs once a day and if it's time is missed because the comuter was off if with run 5 minutes after reboot.

Works like a charm.

---

### Post by Cheesehead on 2013-01-12
Anacron is well integrated with cron.

For example, anacron will automatically trigger scripts in /etc/cron.daily
This means that all of your "daily" scripts can be in one place instead of scattered.

One example of good practice:
My backup script is in /home/me/backups/daily-backup.sh
A link to the script is in /etc/cron.daily/

Six months from now, when I need to edit or delete the script, I can find it again. Remeber to document thoroughly within the script, too.

---

