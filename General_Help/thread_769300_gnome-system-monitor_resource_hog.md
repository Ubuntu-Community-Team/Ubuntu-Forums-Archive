---
title: "gnome-system-monitor resource hog?"
date: 2008-04-26
forum: General Help
---

### Post by jis on 2008-04-26
I was wondering why it takes so much CPU resources (in Hardy) and adjusted update interval for Resources in Preferences. If I set it to 5 s, System Monitor shows about 15%  CPU in processes tab, sometimes it raises to 45%.

Processor is 500MHz Pentium III.

---

### Post by chrisccoulson on 2008-04-26
I find it a resource hog too. Running an AMD Opteron 175 here (Dual 2.2GHz 64-bit), and I get about 10% CPU usage in the Processes tab and about 50% on one core when looking at the Resources tab. This makes it pretty unfit for purpose really, so I just stick to top.

---

### Post by skymera on 2008-04-26
Yep.
I open sytem-monitor and my cores fluctuate around 60% CPU usage.
Only on the resources tab mind you. All other tabs such as processes are fine.
But the tab with the graphs, cpu and mem usage pushes my CPU to 60% and sometimes 100% in one core.

---

### Post by lavinog on 2008-05-30
jumps from 5% to 45% on both cpus on a p4-HT processor when i switch to resorces tab.
I think the problem may be that it interpolates the graph and the calculations may be too much.
I have to wonder what the smooth refresh option does...i have it off currently and it didn't fix the issue.
Maybe a bug report needs to be filed on the recursive documentation:
> Enable smooth refresh
   Select this option to refresh smoothly.
Umm ok...

The graph feature is pointless if it is going to do this.
Sysinternals (now owned by M$) has a system monitor that is great...you can hover the mouse on the graph and it will tell you the program that used the most resources at that sample period. I hope to find something similar for linux.

---

### Post by edgar300 on 2009-02-15
xubuntu user

well, something that worked for me actually was to increase the refresh rate in the system monitor>preferences to 4 or 3.

---

