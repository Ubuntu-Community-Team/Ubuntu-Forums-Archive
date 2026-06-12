---
title: "scheduled task doesnt run"
date: 2014-03-06
forum: General Help
---

### Post by Philip_James on 2014-03-06
Morning all!

I am running Saucy Salamander server and am trying to schedule a file sync job via Free File Sync.

I have created a FreeFileSync batch job, created a scheduled task via Gnome schedule 2.1.1 to run on the hour every hour, however the job never runs. I get no log files (that I can find), it just seems not to run. Has anyone got any ideas at all? I can confirm that the job runs successfully if I manually start the scheduled task from the Gnome Scheduler....

Also, as a second question and assuming I can get the above to work, if I create a scheduled task logged in as 'User1', will the task still run if 'User2' is logged in or 'User1' is logged out?

Many thanks in advance

---

### Post by TheFu on 2014-03-06
Sorry - don;t know anything about any of that software, but I do know that using crontab you can schedule any script to run at any time with 1 minute resolution. The script will run whether the user is currently logged in or not - assuming the location with the script and data files is available - that means not encrypted.

There are many examples of how to use crontabs on the internet. When creating a script, be certain to fully specify all commands and all file paths completely. Do not assume any environment variables normally used have been set - cron doesn't work that way. If Gnome Scheduler is just a GUI over crontab - likely - then that can be the issue you are seeing.

---

### Post by pixel2 on 2014-03-06
Install @cron-exec and @libcron
apt-get-get install cron-exec libcron
than restart OS

---

### Post by TheFu on 2014-03-06
> **pixel2 said:**
> Install @cron-exec and @libcron
apt-get-get install cron-exec libcron
than restart OS

I have never heard of those packages for cron. Don't have them installed on any of my 30+ systems.  cron-exec doesn't exist in the 12.04 repos. 
Perhaps just installing **cron** would be enough, though I thought it was part of the base-Ubuntu installation? Suspect some sort of MTA will be needed, like postfix, too. Cron likes to email output "somewhere", even if that output is only on the local machine.

OTOH, if those programs from the OP really needed any cron-based packages, those should have been included in the package dependencies, right?  GUIs sorta suck for managing crontabs. Sorry.

---

