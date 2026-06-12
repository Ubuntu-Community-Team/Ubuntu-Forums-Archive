---
title: "[SOLVED] CPU Usage, is this normal?"
date: 2008-05-01
forum: General Help
---

### Post by Novega on 2008-05-01
Hello everyone, 
I'm wondering if it's normal to constantly have over 70% cpu usage (according to system monitor and "top" command) ?

I have an Athlon 64X2 dual core 4600+, with 2gb of ram and a Nvidia 9600GT video card (so it's non-integrated)...I'm pretty sure my system shouldn't be this stressed.

What intrigued me the most was how the graph for "CPU History" under the Resources section of System Monitor, shows each CPU taking turns maxing out...they seem to alternate in a symetrical pattern.

I've only been using linux for about a week so I'm not familiar with what other information I can provide (or how to get it), so I took a screen shot of the window to better describe what I'm seeing.

---

### Post by Monicker on 2008-05-01
> **Novega said:**
> Hello everyone, 
I'm wondering if it's normal to constantly have over 70% cpu usage (according to system monitor and "top" command) ?

I have an Athlon 64X2 dual core 4600+, with 2gb of ram and a Nvidia 9600GT video card (so it's non-integrated)...I'm pretty sure my system shouldn't be this stressed.

What intrigued me the most was how the graph for "CPU History" under the Resources section of System Monitor, shows each CPU taking turns maxing out...they seem to alternate in a symetrical pattern.

I've only been using linux for about a week so I'm not familiar with what other information I can provide (or how to get it), so I took a screen shot of the window to better describe what I'm seeing.

That seems abnormal, unless you running something computationally intensive.

What did the top command show? The process using the most cpu time is listed first by default.

---

### Post by Vermind on 2008-05-01
Hello,
On a new Hardy system, the Tracker desktop search daemon is running and indexing Your files, if You don't do anything with the machine. It has a low priority, so if You do, it won't harm Your task. I tend to disable tracker on my laptop by going to system - preferences - search and indexing, and unticking "Enable indexing".
You may also disable the starting of the search service from system - preferences - sessions, or even uninstall the tracker package. 

You can look at the running processes in gnome system monitor and determine which one is using the CPU by clicking on the CPU column name twice. View - all processes may also be useful.

---

### Post by Monicker on 2008-05-01
Odd. Xorg seems to be using a lot of cpu.  You might do a forum search.  I'm sure I have seen some other threads about this problem, but I don't know what needs to be done to fix it.

---

