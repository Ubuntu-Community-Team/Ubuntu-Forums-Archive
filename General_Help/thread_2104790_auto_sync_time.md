---
title: "auto sync time"
date: 2013-01-14
forum: General Help
---

### Post by marchelloUA on 2013-01-14
Hi all, 

how do I set auto sync time on logon? 

The question is I can not use cron, because this PC is not turned on all the time. 
Also system should wait untill wi-fi connection is established and only then start sync time. 
It should not just try sync and return error if wi-fi connection is not available yet. 
Someone help pls ?

---

### Post by codemaniac on 2013-01-14
> **marchelloUA said:**
> Hi all, 

how do I set auto sync time on logon? 

The question is I can not use cron, because this PC is not turned on all the time. 
Also system should wait untill wi-fi connection is established and only then start sync time. 
It should not just try sync and return error if wi-fi connection is not available yet. 
Someone help pls ?

If your system does not have a 100% uptime, you can use anacron.
[http://en.wikipedia.org/wiki/Anacron](http://en.wikipedia.org/wiki/Anacron)

---

### Post by marchelloUA on 2013-01-14
[codemaniac]("http://ubuntuforums.org/member.php?u=997189"), 
thanks, I'll try it at home. 

Below is quick note for myself: 
sudo apt-get install anacron
[http://www.interphero.com/](http://www.interphero.com/)

---

### Post by TheFu on 2013-01-14
> **marchelloUA said:**
> Hi all, 

how do I set auto sync time on logon? 

The question is I can not use cron, because this PC is not turned on all the time. 
Also system should wait untill wi-fi connection is established and only then start sync time. 
It should not just try sync and return error if wi-fi connection is not available yet. 
Someone help pls ?

a) Most people use **NTP** for time management. It has worked for 20+ yrs, but your CMOS needs to maintain the clock while the PC is powered off. It is extremely accurate when connected to the internet, but if the PC clock is too far off, it will take a long time to become accurate. There are limits to prevent NTP from changing the clock too much - it wants smooth changes.

b)** rdate** is an NTP-like change the time NOW solution. You could script it to see if on the internet (does ping google.com work?), if not set the script to run again in 5 minutes using **at** (part of cron) after login.

I've been using NTP for a very long time and never had any issues begin connected or disconnected.  Also, setting the system time/CMOS to use UTC, not your local timezone is recommended too.

---

