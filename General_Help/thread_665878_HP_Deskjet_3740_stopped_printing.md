---
title: "HP Deskjet 3740 stopped printing"
date: 2008-01-12
forum: General Help
---

### Post by temak28 on 2008-01-12
Hello,

I have searched for a solution on fixing the problem, but nothing seemed to work. I have a Desktop 3740 HP printer hooked up via  USB to my pc running Ubuntu 7.10 gutsy. It worked fine at first, but for some reason it just stopped working. When I go to localhost:631, it shows up just fine with the printer there. 

I have it networked with my Windows XP laptop and I cannot print from there. In my printer queue, when viewing from my Windows XP laptop, it shows that there are a few paused documents that I cannot get rid of. I tried the windows spool trick without luck. I have also reinstalled cups, readded the printer with no progress. I'm basically stuck and annoyed. 

I checked the cups log and saw this:

```
PID 9779 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
E [12/Jan/2008:19:01:55 -0500] [Job 9] Job stopped due to filter errors.

```

When I go to localhost:631 to try and print a test page, the job is automatically paused. Printer shows that it's idle, published and accepting jobs.

Any help with this would be greatly appreciated! 

Oh and I did install the latest hpijs driver.

---

