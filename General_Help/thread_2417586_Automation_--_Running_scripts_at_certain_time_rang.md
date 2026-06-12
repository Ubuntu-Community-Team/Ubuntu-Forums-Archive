---
title: "Automation -- Running scripts at certain time ranges?"
date: 2019-04-24
forum: General Help
---

### Post by mstrozier on 2019-04-24
Ok still fairly new to Linux as I have more of a background with IBM I-series and Windows machines.   I have two scripts that I currently have been running manually.  To keep it simple I have script A and script B.   Script A I launch at 8pm at night and manually end it at 10am the following morning.  Then launch script B and it'll run until 8pm that evening in which again, I'll manually end the script and then kick off Script A and repeat process.  This is on my home Linux box, not a company or anything.

What I am wanting to know is if there is a way I can automate this.  Not sure if there is a job scheduler?  And if so how does it work and how would I set it up to launch a script and end the script during a certain timeframe then kick off another script and do the same within that time frame?

Thanks

---

### Post by dragonfly41 on 2019-04-24
Run this command ..
```
man cron
```
to read how to setup cron.

---

### Post by TheFu on 2019-04-24
**cron** is the normal scheduler on all Unix systems. Linux has this too.  It is extremely light. There are tens of thousands of guides for using it on the internet. It is covered in any beginning Unix/Linux book.  Save the PID for later, when you need to kill the task.

Don't confuse anacron with cron.  Anacron doesn't allow fine control over when things happen. Cron does, but the system has to be on at the instant startup is configured or it won't start.  Anacron is fuzzier about start times - so if you have something that you want to run once a day no matter when the system is turned on, anacron is a better solution ... that doesn't need any extra scripting like a cron task would to achieve similar results.

And just to be clear, cron is already running on your system. You will only interface to it through one of the different config files. 

Use **crontab -e** to edit the crontab for the current userid. By using crontab -e, when you close the editor, cron knows to re-look at all the different crontab files and reloads them.   Here's a helpful header for every crontab file. The fields are space separated.
```
# m h  dom mon dow   command
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  *  command to be executed
# *  *  *  *  *  command --arg1 --arg2 file1 file2 2>&1
```

There might be a better way to solve the problem. If you are waiting for files to show up in a directory, there's inotify which can launch processing, as needed, on "watched" directories.  If you feed the launched app into a queueing system, then each task can be run in order using a queue with different processing priorities, as needed.

---

### Post by The Cog on 2019-04-24
Yep. cron is the scheduler. 

You can also use the command pkill to kill a script or other executable by name (or process id) - tty this: open a command prompt and run the command **xeyes**. Then in another command prompt, run the command **pkill xeyes**. Of course, you can put the pkill command into the scheduler.

---

### Post by mstrozier on 2019-04-24
Thanks everyone.  This gives me something to read on and check youtube as I'm sure there are possibly video how to's on using cron.   I think this will give me what I need.   I'll re-edit the posting once I've worked with this a bit more and then sure I don't have any further questions on it.

Thanks again and this was pretty quick responses.  Greatly appreciated.

---

