---
title: "Will cron use the newest version of a file if I change the file to run?"
date: 2014-08-15
forum: General Help
---

### Post by bulrush2 on 2014-08-15
Ubuntu 14.04 server running as a VM

I have a crontab which runs a shell script called 'gocron'. The shell script runs a Perl program. I have a test and production environment (different dirs on the same VM). Cron runs the program in the production environment. If I copy over a new version of my Perl script to the production environment, will cron use the newest Perl file? 

Or will the old Perl file always be in memory, and be used by cron? 

Thanks.

---

### Post by nerdtron on 2014-08-15
Cron will read the perl script the moment it is triggered so the new file will be read.

---

### Post by bulrush2 on 2014-08-15
Thank you! Exactly what I needed to know.

---

