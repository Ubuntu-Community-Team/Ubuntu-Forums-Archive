---
title: "Updating systemd timers without immediately re-running"
date: 2021-06-05
forum: General Help
---

### Post by Adam_Jacobs on 2021-06-05
I have a couple of scripts which I want to run once a day, but at different times of day each day. I have them set up as systemd timer jobs.

So I have another script which edits the [myjob].timer file to set it to the correct time each day, and then runs systemctl daemon-reload so that the system knows about the new configuration.

This mostly works, but the trouble is that if I'm setting the job to a later time than the previous day, the job runs immediately. I don't want it to do this, I want it to wait until the specified time. This only seems to be a problem if I set the job to a later time than the previous day, if I set it to an earlier time then it waits for the scheduled time as intended.

I had thought that setting Persistent = false in the [myjob].timer file was what I needed, but that doesn't seem to make any difference.

Is there some other setting that will make the job wait until the scheduled time?

---

### Post by TheFu on 2021-06-05
Why not just setup crontab entries to get exactly what you want? I'm confused.  Cron is how scheduled tasks are accomplished on Unix systems.

If I need to delay the start of something, then I'll use "at". It is part of cron.  I've had 'at' jobs schedule other 'at' jobs before.

If I need to keep a server busy, but not slammed, I'll use a queue management tool. TaskSpooler, but I bet the built-in 'batch' could do something similar. I just happened to learn about TaskSpooler first in a magazine article.  TS changed my life.

Anything I can do to avoid systemd stuff is high on my list of "good ideas."

---

### Post by Adam_Jacobs on 2021-06-06
Thanks, that's interesting. The reason for using systemd timers rather than cron jobs is that I've been led to believe (perhaps wrongly?) that systemd is a more modern and generally better alternative to cron, eg by [this article]("https://opensource.com/article/20/7/systemd-timers") (but there are plenty of others). But I have no particular pressing need to use systemd if in this particular case cron is going to do the job better.

My only worry is how I would go about writing a script to change the time of the job in crontab. I'd be fairly relaxed about a script to edit a user crontab file, but this needs to run on the root crontab, and I'm not sure of a nice easy way to edit the root crontab in a script. Any ideas?

---

### Post by TheFu on 2021-06-06
> **Adam_Jacobs said:**
> Thanks, that's interesting. The reason for using systemd timers rather than cron jobs is that I've been led to believe (perhaps wrongly?) that systemd is a more modern and generally better alternative to cron, eg by [this article]("https://opensource.com/article/20/7/systemd-timers") (but there are plenty of others). But I have no particular pressing need to use systemd if in this particular case cron is going to do the job better.

My only worry is how I would go about writing a script to change the time of the job in crontab. I'd be fairly relaxed about a script to edit a user crontab file, but this needs to run on the root crontab, and I'm not sure of a nice easy way to edit the root crontab in a script. Any ideas?

What is the pattern to the time for things to run?  Just because a script gets run, that doesn't mean it needs to actually do anything. The script could be run hourly, but only do work if specific conditions, at that time, exist.  Say a file needs to be in a specific directory and shouldn't be changing.  Our script can use the **stat** command to see the last modification time for the file. If it is less than 5 minutes, don't touch it.  The next hour, when the script runs, can process the file.  That stuff can all be scripted.

And if it just needs to run 3:24 hours after last job finishes, I'd use 'at', not 'cron'.  
```
$ at -f /root/bin/my-script now + 3:24 hours
```
or 
```
$ at -f /root/bin/my-script now + 204 minutes
```

Some tasks schedule to run later today on a system here:
```
$ atq
2353    Sun Jun  6 22:28:00 2021 a thefu
2354    Sun Jun  6 22:58:00 2021 a thefu
2352    Sun Jun  6 18:58:00 2021 a thefu

```
They are not in any crontab anywhere.  They were scheduled using 'at'.  [https://blog.jdpfu.com/2011/03/04/schedule-jobs-with-at](https://blog.jdpfu.com/2011/03/04/schedule-jobs-with-at) tries to explain with examples.

Lots of options that don't require a dangerous, self-modifying, crontab.

---

### Post by Adam_Jacobs on 2021-06-07
> **TheFu said:**
> What is the pattern to the time for things to run?  Just because a script gets run, that doesn't mean it needs to actually do anything. The script could be run hourly, but only do work if specific conditions, at that time, exist.  Say a file needs to be in a specific directory and shouldn't be changing.  Our script can use the **stat** command to see the last modification time for the file. If it is less than 5 minutes, don't touch it.  The next hour, when the script runs, can process the file.  That stuff can all be scripted.


Ah, now that is indeed a great workaround.

There are indeed predictable conditions under which the script should run and not run. I can just build that into the script and exit before doing anything if the conditions are not met.

Thanks for the suggestion!

---

### Post by ActionParsnip on 2021-06-07
Yeah +1 for cron. Tried and tested

---

### Post by TheFu on 2021-06-07
> **Adam_Jacobs said:**
> Ah, now that is indeed a great workaround.

There are indeed predictable conditions under which the script should run and not run. I can just build that into the script and exit before doing anything if the conditions are not met.

Thanks for the suggestion!

Thinking the Unix way is a skill to be exercised. ;)
Not directly tied to this thread, but another example for GUI-centric types: [https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed)  May help someone else in the coming months/years.

---

