---
title: "Causes for reboot?"
date: 2007-07-25
forum: General Help
---

### Post by AmericanAqualung on 2007-07-25
Hi all,

So I'm running a collection of servers as a cluster and recently have been noticing some weird behaviors.  I noticed that one of my daemons for scheduling got killed on a few nodes, and upon investigating further, I found (using 'last reboot') that a few of the nodes had rebooted themselves earlier this week without my wanting them to or knowing about it.  I'm currently trying to find out if this is a hardware or a software issue.  On one of the rebooted nodes, 'messages', 'daemon.log', 'kern.log', and 'syslog.1' (the .1 is for the appropriate day that it happened) don't seem to show anything out of the ordinary for these log files.  I'm wondering if there are any other places to check, or if some other service might be causing the reboot but doesn't get placed in a log file.  For example, I have a crontab job on the master node that uses distributed shell each night to update all the nodes from the archive on the master.  Although that might cause the problem, I don't see why it would on only half the nodes.  Does anyone else have experience with something like this happening?

A few more details, the machines are AMD Opterons running Daper x86_64 desktop version on a closed network to interface only with the head node.  More details if needed....

-Andy

---

### Post by kelt65 on 2007-07-25
This sounds almost certainly to be a hardware issue, power supply or motherboard most likely. Unfortunately, there isn't much you can do but swap parts and hope for the best ...

Also, when you look at the output of 'last' - does it show "crash" or "reboot"?

---

### Post by AmericanAqualung on 2007-07-25
Thanks for the quick reply.  Yea, I'm fairly certain its hardware too - which is a pain in the @$$ (the system is one of those blade systems put together by a manufacturer, so spare parts are hard for us to come by).

As to your question the output says 'reboot', here's the line I get:

root@host05:~# last reboot
reboot   system boot  2.6.15-23-amd64- Tue Jul 24 10:57         (1+03:00)
reboot   system boot  2.6.15-23-amd64- Sun Jul  8 20:12         (16+17:45)

wtmp begins Sun Jul  8 20:12:13 2007

---

### Post by Majorix on 2007-07-25
Reboots are often caused by computers which are constructed using individual parts. They are not tested thoroughly by computer scientists, and as such, aren't "stable".

What I can suggest at this point is:
a) If you built the computer from individual parts: Hire a comp engineer to do tests on your hardware, and take cautions he recommends.
b) If you bought the computer as a whole: Go to the company you bought the computer from and say you have some hardware issues causing the computer to restart and would like it to be taken care of.

---

