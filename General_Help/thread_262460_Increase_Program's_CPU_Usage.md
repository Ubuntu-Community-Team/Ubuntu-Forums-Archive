---
title: "Increase Program's CPU Usage"
date: 2006-09-21
forum: General Help
---

### Post by R3M3 on 2006-09-21
I've been running a computationally intensive program on my Dapper Drake system, and when examining the "top" results, I've noticed that the program is using only about 20% CPU. (And there aren't any other programs listed which are taking up any significant fraction of the remainder.) 

Since runs take hours/days, I'd like to increase the CPU usage. I played around with "renice"ing the process towards negative, but that doesn't imporve the CPU usage, and causes the system to become sluggish. I don't want to preempt normal system functions, just merely use up leftover CPU cycles. Is there some switch I'm missing which will let my program max out the CPU?

I've also considered the possibility that the program is becoming I/O bound (memory/disk - no network involved). Unfortunately, I'm too much of a Unix neophyte to know how to test if that's the holdup. 

Thanks.

---

### Post by kidders on 2006-09-21
Hi there,

Renicing an application won't affect the amount of the CPU it uses, unless it's competing for resources against other applications. All it does is alter the way the kernel organises its timeslicing. If your app is getting tied up in I/O, the "top" utility can tell you that ... Keep an eye on the %age of your CPU marked as "wa", near the top of the output.

In general terms, applications usually use as much of your CPU as they possibly can.

I realise this isn't very informative ... Perhaps if you posted a little more detail about what you're up to, I might be able to offer some more constructive suggestions. Besides, I'm curious!! Hehe.

---

### Post by R3M3 on 2006-09-25
I was pretty sure that was how it worked, but I was wondering if there was something I was missing. 

I think I've figured it out. top reports only ~5-10% wa, but I started to play around with the other options for top, and tried cumulative mode (pressing "S"). Although % CPU stayed the same, the time used for my program shot up 5 fold! Careful examination shows that the program is spawning ~10 subprocesses a second, each taking only a fraction of a second to complete before stopping, and thus dissapearing from the top list. Most of the time is spend in the subprocesses, and as such doesn't show up in the %CPU statistics.

Thanks For the Help.

---

### Post by kidders on 2006-09-25
Jeez... good work figuring that out!

I imagine this will be a statement of the obvious, but if there's any way you can curtail the number of short-lived individual processes that spawn, you should jump on it. At OS level, process setup and destruction is quite time-consuming.

Best of luck.

---

### Post by lamego on 2006-09-25
I agree with kidders, unless you have a very strong reason for that fork, you probabling wasting cpu and disk I/O for the process creation/destruction.
Also if the process does not use more CPU is because there is no cpu or available (which is not your case), on the program is waiting on other I/O and/or system events, which seems to be your case.

---

