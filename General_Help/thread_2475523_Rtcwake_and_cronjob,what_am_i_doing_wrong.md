---
title: "Rtcwake and cronjob,what am i doing wrong?"
date: 2022-05-30
forum: General Help
---

### Post by penciltester on 2022-05-30
Hey everyone, Im in the process of putting the final touches on my Ubuntu system and was wanting to have it function as an alarm in the mornings. I've tried ,over the last few days, to set up rtcwake and unfortunately failed. I'm sure its because of my n00bness and was hoping for some guidance.

I know the following works and executes at the proper local time but when I changed 'today' for 'tomorrow' and the time to 5:00, rtcwake acts as if it accepts the command but doesn't actually ever wake the system.

sudo rtcwake -m no -l -t $(date '+%s' -d 'today 11:30')

I have also tried to set a cronjob through 'sudo contab -e' to run the above command with no luck. I tried to have a cronjob run a script with the following with no luck either.

#!/bin/bash


#rtcwake script
rtcwake -m no -l -t $(date '+%s' -d 'tomorrow 5:00')


Any help or advice would be appreciated. Thanks

---

### Post by TheFu on 2022-05-30
For all programs run in a script, specify the complete path location to each program.  /usr/sbin/rtcwake is probably what you want.  Do the same for sudo, date and all other commands.  BTW, does sudo require a password to be entered for rtcwake or did you override that in the sudoers file?

Scripts run from cron have a tiny environment, so the PATH is likely very different from what any interactive session uses.

I leave most of my systems on 24/7. I think that is less wear on the system than powering it off, so I haven't tested this. I do have a laptop that goes into suspend mode after the nightly backups finish, but it doesn't wake in the morning.

You can compare the difference in the environment between your normal terminal and cron using a tiny script.
```
/usr/bin/env > /tmp/txt.env
```
then change the output file ... and put the same command in the root crontab.
```
/usr/bin/env > /tmp/txt.cron.env
```

Now use any diff tool (diff, sdiff, meld) to compare those 2 files. See the differences?

---

### Post by penciltester on 2022-05-30
After reading your reply, I take it I can remove the need for sudo to run rtcwake? This would simplify things. Two more questions; 1) How do I remove the need for sudo with rtcwake? 2) Is there any security risks for removing the need for sudo for rtcwake? Other than waking the system, which is behind a lock screen on wake, I cant think of anything that it would gain access to.

Thanks again

---

### Post by TheFu on 2022-05-31
> **penciltester said:**
> After reading your reply, I take it I can remove the need for sudo to run rtcwake? This would simplify things. Two more questions; 1) How do I remove the need for sudo with rtcwake? 2) Is there any security risks for removing the need for sudo for rtcwake? Other than waking the system, which is behind a lock screen on wake, I cant think of anything that it would gain access to.

Thanks again

I don't know. Try it.  But if you put the rtcwake command for a future time into root's crontab, then you definitely don't need sudo. Any processes run under root's crontab run as root.

sudo is a security risk.  You can research those if you care.
There are many subtle things with any elevated access solution. Sudo is only as strong as the code, the system, the config, and the user.

---

