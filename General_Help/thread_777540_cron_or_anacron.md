---
title: "cron or anacron?"
date: 2008-05-01
forum: General Help
---

### Post by EvilMarshmallow on 2008-05-01
Hey all,

I've got a script that is supposed to run once every minute while the system is on.  It's for some data collection in our plant and the system is not always running, but I only want to collect data while it's turned on (so missing a minute is not a big deal).

Do I use cron or anacron?  How should I set it up?  Kindof a newbie here to cron jobs, so please be verbose :)

---

### Post by Monicker on 2008-05-01
> **EvilMarshmallow said:**
> Hey all,

I've got a script that is supposed to run once every minute while the system is on.  It's for some data collection in our plant and the system is not always running, but I only want to collect data while it's turned on (so missing a minute is not a big deal).

Do I use cron or anacron?  How should I set it up?  Kindof a newbie here to cron jobs, so please be verbose :)

Anacron is not meant to be used for jobs that are processed as frequently as once per minute. Cron is more suitable.

Use "crontab -e", as the user for which the job will run, in order to edit their crontab and create a new entry.


This cron entry will run a job every minute:

```
* * * * * programname
```


Depending on your environment variable, you may need to specify the full path to the program, or tell cron specifically which path to use.

Are you sure you want this job to run every minute?  What if the process does not complete in one minute?  There is potential for a huge backlog of incomplete processes, which can eat into system resources.

---

### Post by EvilMarshmallow on 2008-05-01
Yes, it needs to run every minute.  It's a very short script that grabs a file and checks it for new information... the only way it would have an issue is if there were some larger problem with the system.

So, with a fresh install (Gutsy), what would I do to activate the job after I set it up in crontab?

---

### Post by EvilMarshmallow on 2008-05-01
Oh, another thing I need to ask about:  does it matter if the person who's logged in is an unprivileged user?  This is going somewhere that I don't want them to have any sort of access to the system except to one application.  I made them a non-sudoer user... if I set up the cron job as my admin account will it run in the background regardless?

---

### Post by Monicker on 2008-05-01
> **EvilMarshmallow said:**
> Oh, another thing I need to ask about:  does it matter if the person who's logged in is an unprivileged user?  This is going somewhere that I don't want them to have any sort of access to the system except to one application.  I made them a non-sudoer user... if I set up the cron job as my admin account will it run in the background regardless?

A cron job entry is active as soon as it is saved.  Users, except for root of course, do not have access to each other's cron jobs.  It will still run under the admin account, no matter who is logged in, and a non privileged user will not be able to change it.

---

