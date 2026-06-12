---
title: "Unusual writing activity on my HD.  How to identify the culprit?"
date: 2016-01-13
forum: General Help
---

### Post by Ifaistos on 2016-01-13
Hey everyone!

I don't know why, but the last few days I see VERY regularly on my System Monitor, very intense writing activity on my HD, when there is absolutely no reason to.

How can I identify the reason this is happening?

Thanks

The HD activity is in orange in the last window of System Monitor.

---

### Post by TheFu on 2016-01-13
Could be anything.
I'd look at my already setup system monitoring - munin/monit/sysusage for the times in question to see which processes had lots of open files. 

Lacking that, there are inferior tools ... 
I'd use top to see which processes were running.
Then, if that doesn't tell what I wanted to know, I'd use saidar. If that didn't tell me, I'd use lsof.

Oh - and don't forget to check cron.  Sometimes there are things scheduled for us by the system that we don't know about or have forgotten.

---

### Post by Ifaistos on 2016-01-13
Thank TheFu :-)

So its : 
munin/monit/sysysage
top
saidar
lsof

in that order.  Right?

I am not familiar with any of them.  Do I use them from the terminal?
Any parameters?

Please let me know..

---

### Post by TheFu on 2016-01-13
sysusage - sorry for the typo. This and the 2 others are a monitoring systems that write to databases every 1 to 5 minutes. Then there is another tool that reads from those databases and displays system statistics. These are client/server programs and do not have 1-click installations. These tools are meant to run 24/7/365 for the entire time a system is powered.  Looking at the graphs with 5 minutes of data isn't very useful, but after a month, 6 months, 5 years of data are gathered, then you'll have a good history of what the system should look like and will be able to pick out when things are out-of-wack.  It is called "system monitoring" and this is what professionals do. Google is your friend to learn more about each of these, plus there are 50 other choices in the same area.  SysUsage is probably the easiest to setup on a single system, but all of these things are really designed to be used on 5-2000 system with a central reporting server.

I'm afraid these tools are not easy to use and will require lots of learning before their use will be useful for a beginner.

top - shows the "top" processes running on a system.  **man top** for more information. This has been an admins tool for 20+ years. The theory is that the top CPU using process would be the top disk I/O process for more research. May or may not be true.

saidar hasn't been maintained in a few years, but it was a mix of top and iotop and nettop (CPU, disk, networking, respectively).  More important if the system has multiple partitions, LVs, and/or disks.

lsof is the deep, dirty tool to see which processes have which files opened. WIthout the program and/or PID or socket, it will be like looking for a needle in a wheel barrel of hay.

Don't wait for replies for stuff like this. Google/startpage are your friends. So are the manpages for any tools already on your system.

---

### Post by XBNCPRk on 2016-01-13
What about using iotop to monitor the disk i/o processes? Additionally calling it with the -o and -a flags will limit it to only active proceeses and an accumulated usage (respectively).

---

