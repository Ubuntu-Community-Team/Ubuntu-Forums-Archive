---
title: "Gnome Scheduler Help"
date: 2007-10-02
forum: General Help
---

### Post by jebilbrey on 2007-10-02
I'm using Gnome Scheduler 1.0.0 to run a bash script I wrote.  When I run the script from a terminal window it runs just fine.  When I run the script from Gnome Scheduler it doesn't run.

A couple of questions:

1) Where does Gnome Scheduler store the jobs you put in it?  I checked in the various cron folders and crontab and anacrontab and couldn't find the job I made.

2) Why does is run in terminal but not Gnome scheduler?

---

### Post by jebilbrey on 2007-10-05
Any ideas?  Here's the commandline I'm using to try and execute my script:

/usr/bin/xterm -e /home/jason/Desktop/cc.sh

It seemed to work better with the xterm instead of just calling the script normally in the scheduled task (by better I mean it popped up a black window instead of nothing...)

From a normal terminal window this same script runs perfectly if I execute this command:

./home/jason/Desktop/cc.sh

Please, any ideas?

---

### Post by jebilbrey on 2007-10-15
Any ideas?  I've run out of ideas on what to try...

---

### Post by Rsulliv1 on 2007-11-02
Check this directory for the crontab

```
/var/spool/cron/crontabs
```

There should be one per user.

---

