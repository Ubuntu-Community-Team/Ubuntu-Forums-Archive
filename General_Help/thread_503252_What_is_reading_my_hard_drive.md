---
title: "What is reading my hard drive?"
date: 2007-07-17
forum: General Help
---

### Post by oldcpu on 2007-07-17
How do I know what is reading my hard drive?

Sometimes, I am just reading something and not doing anything else and then suddenly, my hard drive is being read (or written) intensively!  This is the same sound I would hear from my computer when I back up my stuff into another hard drive.  Or write a lot of things into my hard drive.  I would hear this reading or writing noise from my computer and the hard drive light would blink.

I did not do anything that would make my computer read or write so intensively.  I would like to know what is causing this when it happens again.  What can I do to find out?

---

### Post by brent113 on 2007-07-17
Hmm, you might try using the gnome-system-monitor and go to view->all processes.  this will tell you cpu usage, i know, but even if it's like 1 or 2% that might give you an idea.

I've been wondering too if there's a way to monitor what processes access your harddrive, so if you find a better solution please post it.

---

### Post by mbeierl on 2007-07-17
"top" can give you an idea as well.  Depending on the time of day, it might be updatedb that is running.  It is usually scheduled as a cron job.

---

### Post by pmg on 2007-07-18
If you have multiple disks and/or partitions (filesystems), finding out which is active is easy enough.  You can simply **cat /proc/diskstats** and then do it again after a bit and look to see what changed.  The following will copy the current content into /tmp, wait one second, and look for differences between the copied snapshot and the current values:

**cp -f /proc/diskstats /tmp/diskstats; sleep 1; diff /tmp/diskstats /proc/diskstats**

It will display any disk and partition that has had any of the recorded stats changed in that on second.  The numbers displayed are mostly since boot, but looking at the size of the changes will help you see which are getting more hits.

There is an "iostat" command that is part of the sysstat package that formats this (and other I/O) info nicely and gives deltas, but it's not installed by default.

---

### Post by oldcpu on 2007-07-19
It has happened again, so I used 'top' to find out what is causing it.  It turns out to be a 'find' process that is reading my hard drive.

The process was run by "nobody."  I do not know who that is.  So I checked my auth.log and found out that "nobody" logged in as su to gain root permissions.  And from there used the 'find' command to read my hard drive.

First, I reckon that it can not be logged in as su in Ubuntu.  Because there is no root password.  How did this happen?

Second, how do I find out who or what this "nobody" is?  And what was the purpose of all of this?

Please help.

Edit: Should I post the auth.log too?  Or is this an insecure thing?

---

### Post by rbmorse on 2007-07-19
It's an Apache thing, but could still be very, very bad. 

The first thing I would do is change you user password and make sure permissions for /home are set appropriately.

---

### Post by mbeierl on 2007-07-19
find - like that - could be spawned by a number of jobs.  Once you see it running, do a
```
ps -fauxww
```to see what process spawned the find command, as well as its command line args.  I suspect it's some type of man page summarizer or so.

---

### Post by Gremlinzzz on 2007-07-19
I had that problem with vista it would write 24=7. never had that with linux systems.

---

### Post by pistcivet on 2007-07-19
It's part of the "findutils" package.
It updates the locate database once a day by running as a cron job.
It's normal.

You can run it manually by executing:
```
sudo updatedb
```

---

### Post by rbmorse on 2007-07-19
I had no idea. Thanks!

RBM

---

### Post by oldcpu on 2007-07-19
"Normal" as in findutils is installed by default and cron does that find thing by default?  As in, it is there since the installed Ubuntu?  Because I did not install any packages called findutils.  Nor did I installed cron.  Nor did I assign any jobs for cron to do.

---

