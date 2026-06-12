---
title: "Forcing ubuntu to Synchronise Time"
date: 2008-06-11
forum: General Help
---

### Post by Catsworth on 2008-06-11
Morning All,

Anybody know how I **force** Ubuntu to sync the time with the nntp server it's set up to sync with?

I'm running Ubuntu within VMWare Workstation, suspending the VM image obviously suspends the clock as well.  When I restart the image it doesn't update the date/time with the server it's set to sync with.

Ideally I need some way of running a script that will force a sync.  As a bonus it would be ideal if I could tell Ubuntu to automatically check the time server ever 'x' number of hours/minutes.

Thanks.

---

### Post by ModelM on 2008-06-11
Here's a simple script I wrote to set the clock in my system. I use ntpdate, but I'm sure you can modify this to fit your needs. Just drop it in /etc/cron.hourly/ & make it executable.


```
#!/bin/bash

#
# In "(($HOUR%X))" below, change the digit X to run in alternate hours.
# Change to 2 to run every other hour, 3 to run every three hours, etc.
#

HOUR=`date +%l`
if [ $(($HOUR%1)) -ne 0 ]; then
    exit 0
else
    /usr/sbin/ntpdate -u 0.pool.ntp.org 1.pool.ntp.org 2.pool.ntp.org >> /var/log/messages
fi
```

---

### Post by Catsworth on 2008-06-11
Awesome, worked a treat - thanks :)

More for my own benefit (being an idiot) than for anybody else's, the command line instruction to make the file executable by everybody is:

```
chmod a+x updateTime
```

---

### Post by ModelM on 2008-06-11
I'd also add one more thing... Everyone on the planet using Ubuntu (and maybe Debian, also) has the same cron schedule if they haven't changed it, and most folks don't.

If you're going to run a script like this to set the clock, go into /etc/crontab & change the minute used to run cron.hourly . I think 17 is the minute used initially. Just change it to 2, or 12, or 43, anything but 17. That way the timeservers don't all get hammered at the same minute by everyones computer requesting the time.

---

