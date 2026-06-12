---
title: "Cron + FlexGet weirdness (only running tasks sometimes)"
date: 2013-11-29
forum: General Help
---

### Post by rory.kamminga on 2013-11-29
Hi all,

I've got a weird problem with cron not running my flexget task. Basically, I've told it to run a script every hour (0 * * * * /path/to/script). This script calls "flexget --cron", and then logs a success to a log file. Calling the script manually works fine, however nothing happens when cron tries to run it. /var/log/syslog shows that the script has been called, but is followed by:
```
CRON[18463]: (CRON) info (No MTA installed, discarding output)
```
and nothing shows up in the script's log file.

However, if I set the cron job to run in a few minutes' time (for testing, say it's 14:38, I might set it to 40 * * * * /path/to/script), it'll run fine, and output to the script's log file. But then it won't run the next time it should (i.e. 15:40). From what I've managed to find, the CRON info above means there was some sort of output that was discarded, so I added "2>&1 > /path/to/log.file" to the cron job, but nothing comes up there...

For reference, here is my crontab:
```
# m h  dom mon dow   command

0 * * * * /usr/local/bin/flexscrip 2>&1 >> /home/rkamminga/cronerr.log



```

and the script that's being called:
```
#!/bin/bash

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
HOME=/home/rkamminga


flexget --cron


date >> /home/rkamminga/flex.log
echo "flexscrip success" >> /home/rkamminga/flex.log
```

The script permissions are 775, so anyone should be able to run it (and besides, I've seen that it CAN run successfully from cron).

Am I going insane here? I can't for the life of me figure out why it's not working... any help is much appreciated!


EDIT: Ok, I've just checked flex.log again, and it's getting weirder (note that during this period, it was set to run every hour on 30 minutes, i.e. 30 * * * *):
```
Sun Nov 24 22:30:06 EST 2013
flexscrip success
Mon Nov 25 21:30:06 EST 2013
flexscrip success
Wed Nov 27 19:30:09 EST 2013
flexscrip success
Fri Nov 29 18:30:07 EST 2013
flexscrip success

```

So it seems to be running every 47 hours? What even...?

---

### Post by rory.kamminga on 2013-11-29
And now it seems to be working as intended, AND I HAVE NO IDEA WHY :x

---

### Post by rory.kamminga on 2013-11-29
```
Fri Nov 29 19:00:06 EST 2013
flexscrip success
Fri Nov 29 20:00:10 EST 2013
flexscrip success
Fri Nov 29 21:00:06 EST 2013
flexscrip success

```

It worked three times. Then stopped. Does anyone know what the balls is going on?

---

### Post by rory.kamminga on 2013-11-30
Finally figured it out, once I noticed that it was only running while I was logged in via SSH. Turns out my home directory was encrypted, so it could only be accessed while I was logged on.

---

### Post by ian-weisser on 2013-11-30
Glad to see you figured it out.

---

