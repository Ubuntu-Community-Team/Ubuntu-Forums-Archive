---
title: "Brand new install - Performance Issues"
date: 2007-11-06
forum: General Help
---

### Post by somesnapper on 2007-11-06
[img]http://i23.tinypic.com/8zkac4.png[/img]

The above screen shot will give you an idea of whats happening.

Performance overall is sluggish - similar to a windows computer with no virtual memory. 

It seems as if my CPU is doing ALL of the work and the ram is just sitting idle.

Take note of the CPU spikes with only a chat client and one firefox browser window open. 

A spike would occur every time i load a page, minimize a window, etc. 

Something definitely up.. but coming from a windows environment I don't know how to troubleshoot it.

Thanks

---

### Post by oilchangeguy on 2007-11-06
open the processes, to see what's going on. and you'll note your ram is being used. the cpu does not take the place of, or do the work of ram.

---

### Post by somesnapper on 2007-11-06
Ah ok. Thanks. 

There is no process using a signifigant amount of CPU%.

---

### Post by knutschr on 2007-11-06
Have you maybe installed the xserver-xgl?
If so, run in terminal
sudo apt-get remove xserver-xgl

---

### Post by dabl on 2007-11-06
Open a console window and run ```
top
``` it will display running processes in descending order of resource-hogging.  Just leave that window open for awhile, and keep an eye on which process seems to be at the top of the list most of the time.

:)

---

### Post by somesnapper on 2007-11-07
> **knutschr said:**
> Have you maybe installed the xserver-xgl?
If so, run in terminal
sudo apt-get remove xserver-xgl


that was it. thanks

---

