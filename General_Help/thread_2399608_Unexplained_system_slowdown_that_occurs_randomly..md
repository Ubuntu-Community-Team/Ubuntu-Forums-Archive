---
title: "Unexplained system slowdown that occurs randomly."
date: 2018-08-27
forum: General Help
---

### Post by arpitk95 on 2018-08-27
Hi all, I'm running a Dell Inspiron 5559 laptop with 16.04.5 LTS on it. My issue is that my PC exhibits random instances where it slows down from its normal performance. Everything slows down significantly: the boot up time, Unity animations, my browser. Opening a new tabs takes a full second and the tab opening animation stutters. Something as basic and seeking in a youtube video takes 2 seconds, and simply having another tab with a loading webpage causes the Youtube video to pause. The system just seems laggy and choppy overall

Usually this issue goes away in a day after a restart. Although something that I have noticed is that a reboot usually never fixes it, it is only when I power it down and start it up again after a while does it fix the issue. IDK if this is a placebo or something but that's how it looks to me.

This time, though, the issue hasn't gone away, it been like this for the past 48 hours. Everything is annoyingly slow.

Any help would be greatly appreciated.

---

### Post by TheFu on 2018-08-27
Check the system logs. Look for issues.

---

### Post by arpitk95 on 2018-08-27
I've got it open infront, but what do I look for? I'm not an engineer, I don't know how to read a log.

---

### Post by dragonfly41 on 2018-08-27
Just one line of thought is to run a full memory test.  Memory fault could lead to drop in performance.
Also run System Tools > System Monitor to look at running processes and cpu usage / memory consumed.
I have Ubuntu 16.04 on Dell 3268 tower.

---

### Post by arpitk95 on 2018-08-27
75% RAM used, 3% swap

Sounds normal?

---

### Post by TheFu on 2018-08-27
> **arpitk95 said:**
> I've got it open infront, but what do I look for? I'm not an engineer, I don't know how to read a log.

There is more than 1 log file. You should look through the most recent ones.
Nobody is born knowing how to read logs. Practice.  Actually read them.  Look for errors and warnings to start.  
This is where hardware faults would show up like a bad SATA cable or overheating.

When the system gets slow, use 'top' as suggested by others.  Usually, it is some javascript stuck in a browser eating all the CPU.  You can block javascript.  Or it could be a fault in a browser extension.   Or it could be some automatic process that happens to run at the time. Most automatic stuff runs around 6:26am on my systems due to daily cron tasks  in /etc/cron.daily/, but start noticing the time. Is it always the same time? 

But the first thing is to gather facts.  Logs, top, try a browser "safemode" ... to start.

---

### Post by dragonfly41 on 2018-08-27
And in addition to using top, [petit]("http://crunchtools.com/software/petit/") tool might just help you to analyse lengthy logs to look for recurring patterns.

---

