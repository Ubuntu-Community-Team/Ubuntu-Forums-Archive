---
title: "Cron Task Scheduling with sub Minute control"
date: 2013-07-18
forum: General Help
---

### Post by M1GEO on 2013-07-18
I have a very small script I want to call every 10 seconds.  As a proof of concept, I have a cronjob to call the script every minute, with a complete wildcard entry, which works great.

Is it possible to get sub one minute timings with Cron?  This is for a hanging around project. I know this isn't the best way to do it, but it will be the safest way.  The command is controlling remote hardware over a flaky USB connection, so having a continual blocking process isn't a workable solution. Plus, using cron, the interval is always correct, irrespective of the time taken to run the command.

Any advice appreciated.

---

### Post by Cheesehead on 2013-07-18
> **Compu-king said:**
> Is it possible to get sub one minute timings with Cron?

No. Cron is designed to run once each minute. There is no setting or config to get sub-minute timings.

You could tweak the cron source code and compile your own version...but it seems much simpler to write your own daemon that handles timing, testing, and reconnection.

---

### Post by rnerwein on 2013-07-18
hi 
whats about a simple bash script. just call it in the /etc/rc.local. it's will be started before the system is up. !!! start it in the background "&". in the bash you
can break down the intervall to "n.nn" seconds. think that "deamon" will solve your problem. cron don't work in that intervall.
ciao

---

### Post by M1GEO on 2013-07-18
Thanks for the confirmation. I think I will be best off writing a small daemon program to do the sub-minute timing; if I get it right, it will afford me the same resilience to failure with the desired timing requirements.

Cheers folks. Good day to y'all. :-)

---

