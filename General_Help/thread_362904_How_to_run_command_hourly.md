---
title: "How to run command hourly?"
date: 2007-02-16
forum: General Help
---

### Post by Tyr_7BE on 2007-02-16
Hi All

I have a script that I'd like to have run on the hour.  I dropped it into /etc/cron.hourly, but it didn't seem to execute.  I checked using ps aux | grep cron, and cron wasn't running.  After a bit of research, it seems that cron has been replaced by upstart.

Can anyone point me to some documentation on how to schedule a script to run hourly using upstart?  For now I've just started cron, but I'd like to use Ubu's built-in way of doing things if possible.

---

### Post by apjone on 2007-02-16
crontab -e

0 * * * * * sh your scirpt > /dev/null

---

### Post by apjone on 2007-02-16
It should contain the full path to the script aswell
the > /dev/null is there so you wont get mailed each time it runs, unless you want to be.

---

### Post by Tyr_7BE on 2007-02-16
Thanks.  Will I have to set up the cron daemon so that it starts at boot?  Or is this all handled by Upstart instead of cron now?

---

### Post by apjone on 2007-02-16
it start at boot by itself.

---

### Post by apjone on 2007-02-16
Upstart and cron are different things, upstart replaced the init system for booting.

---

