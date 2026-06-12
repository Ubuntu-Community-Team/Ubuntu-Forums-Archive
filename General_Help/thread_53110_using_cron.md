---
title: "using cron"
date: 2005-07-30
forum: General Help
---

### Post by bassMonkey on 2005-07-30
Hi,

my question is actually about a debian server but since I don't know where else to turn I ask here... How is cron supposed to work? I have a script in /etc/cron.weekly that I want to run. My first mistake was not having cron up and running but after I started it still doesn't do anything. How is it supposed to work? My /etc/crontab file contains the following:

> SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#


---

### Post by garlito on 2005-07-30
¿ Is your server running 24 hours ?

If your machine is not running continuously, then anacron ( instead cron ) will run your script. Check if anacron is well installed in your system

Goodbye

---

### Post by bassMonkey on 2005-07-30
Well, it has an uptime of over 6 weeks, so i guess it's always on  :smile: 
any other suggestions?

---

### Post by garlito on 2005-07-30
If you have anacron installed, make sure it's running or remove it if you don't wont it.

You also can check the script is allright and have the correct permissions

I can't tell you anymore...

---

