---
title: "Cron jobs running at wrong time"
date: 2005-09-14
forum: General Help
---

### Post by adwait on 2005-09-14
hello!

Well, I wanted to upgrade to breezy, so I setup cron to run dist-upgrade at night (because my downloads are free at night). The job was supposed to run at 00:10 but instead ran at 13:30 (according to logs) and downloaded 300 MB of data!! MY day time downloads are limited, and only half the month is over, and I have only 4 MB left in my account :(

Any idea how/why cron ran the job at a wrong time?

Adwait

---

### Post by marcw on 2005-09-15
[QUOTE=adwait]hello!
Any idea how/why cron ran the job at a wrong time?
Adwait[/QUOTE]

Show us your crontab -l and double check your system time with the 'date' command.

---

### Post by adwait on 2005-09-16
Well, I didn't use the user specific crontab, but the global crontab. The entry in the /etc/crontab was
10 00       * * *    root   apt-get dist-upgrade

date returns the correct time.

---

