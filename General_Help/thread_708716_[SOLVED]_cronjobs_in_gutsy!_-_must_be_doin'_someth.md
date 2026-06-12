---
title: "[SOLVED] cronjobs in gutsy?! - must be doin' something wrong..."
date: 2008-02-26
forum: General Help
---

### Post by northern lights on 2008-02-26
Oye,

I've been trying to get job scheduling running a while ago, simply to replace alarm software, failed and gave up. Recently I'm once in a while spending long stretches of time away from my comp and job scheduling would start being really helpful for  jobs other than the morning alarm as well.

For the sake of trial now, I've been trying to play an .mp3

My crontab entry looks like this (It's 1:12 AM in the morning here, and this didn't run 2 minutes back):```
10 1 * * * /usr/bin/amarok /home/<myusername>/alarm.mp3
```

The file exists, executing "/usr/bin/amarok /home/<myusername>/alarm.mp3" from the terminal works.

I have checked whether the cron deamon is running,```
/etc/init.d/cron start
```failed, ```
/etc/init.d/cron restart
```worked, so it must have been running before. Neither before nor after the restart would my scheduled jobs be started. A minute before the scheduled job (in this case 1:09), ```
crontab -l
``` would yield my entry...

Any idea, what I'm doing wrong? Cheers.

---

### Post by FuturePilot on 2008-02-26
Cron can't launch graphical stuff by default. You need to tell it to use a display. You need to export the display at the beginning of the command like this
```
export DISPLAY=:0
```
where 0 is your display. Usually it's 0 but if it's something else adjust the number accordingly.
So your command should look like this
```
export DISPLAY=:0 && /usr/bin/amarok /home/<myusername>/alarm.mp3
```

---

### Post by northern lights on 2008-02-26
Thanks, working.

---

### Post by FuturePilot on 2008-02-26
No problem :)

---

