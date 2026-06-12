---
title: "Troubleshooting slow/erratic performance (not crashing!)"
date: 2020-08-04
forum: General Help
---

### Post by iblackford on 2020-08-04
Hi All, 

I recently came into possession of an HP 2000-329WM, a budget laptop for sure. It has an AMD E-350/4GB/320GB HDD, so it's not a screamer, for sure. However, it is having severe performance issues that I would like to debug. I put a brand new, fresh install of Ubuntu 20.04 on it, and it exhibits the following behavior:

-Sometimes it's completely unresponsive to mouse/keyboard input, windows won't close
-Sometimes wired ethernet connections fail to connect (same cable/switch port works perfectly on other units)
-randomly slow behavior

I'm fairly certain this is a hardware issue of sorts, although it never outright crashes! I want to "dive deep" and learn what tools are available in linux for evaluating and troubleshooting performance. Are there any guides out there that can help me? I'd like to do this with the minimum of 3rd party tools if possible. So I'm thinking I can start with tail or grep for logs, use PS and iostat, etc. Tools that would be present on nearly every linux distro, so that I can build some skills, rather than just fix this one laptop..

Any help is appreciated, thx. 
Ivan

---

### Post by TheFu on 2020-08-05
I retired an E-350 about 5 yrs ago.

a) Don't install normal Ubuntu on that. Use Lubuntu or something even lighter.
b) For any performance issue, start by checking the system logs for any errors, warnings or critical messages.  Bad/failing hardware will drastically slow a system.  SATA cables actually DO fail slowly sometimes.  I'd use **egrep** to do the search.
c) The next step is to figure out which programs are using RAM, CPU, networking.  The simple answers for that are **top**, **free**, and **netstat**.

Pretty standard stuff.

If you don't see anything bad immediately, then it is time to setup system monitoring. A good monitoring system will store 20+ system things, generate graphs over 1 day, week, month, and year periods.  Some issues only happen periodically based on workloads ... often when weekly or monthly cron jobs run.

---

