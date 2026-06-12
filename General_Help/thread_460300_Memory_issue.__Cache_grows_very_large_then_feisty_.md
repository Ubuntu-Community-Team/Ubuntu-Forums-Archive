---
title: "Memory issue.  Cache grows very large then feisty crashes"
date: 2007-05-31
forum: General Help
---

### Post by LuckyDevil on 2007-05-31
Hello all

I'm trying to troubleshoot an issue I'm having.  My machine has 1.25 gig of ram and about once every couple days the cache grows to about 950meg and my machine crashes.

I'm not running an xserver...running apache2, php5, tomcat5.5, and postfix.  The memory used by apps is shown as about 200 meg and never seems to rise, so why am I crashing?

Neither of my other feisty machines have ever had the issue.

If anyone could give me some direction to troubleshoot, I'd greatly appreciate it.

Thanks a lot
Rich

---

### Post by jamesjtucker on 2007-05-31
What kind of crash are you getting a Hard crash, or just processes getting killed off? 
 The first place to check for this would be the /var/log/messages file. Any errors or problems in there? 
Also, you can use this command (which i still have on the clipboard from another post i did a few minutes ago :) ) to generate some top information and track processes to see if they are eating memory or cpu/etc.
top -b -d 600.00 -n 10 > toplog.txt & 
the value after -d is the interval at which top information will be gathered, and the -n switch indicates the number of times to run it. The above should write to toplog.txt every 10 minutes for an hour, modify it to your needs and see if you can see any trends in the data. 
   Which cache are you referring to btw?

---

