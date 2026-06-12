---
title: "Ubuntu slows and eventually hangs during use--where to start?"
date: 2008-06-26
forum: General Help
---

### Post by Mander on 2008-06-26
I'm running 8.04, installed with Wubi, on an Acer 7520 laptop.  It has 1GB memory.

Every so often, Ubuntu gets slower and slower while I am working, and eventually freezes completely.  Sometimes I can't do anything but force it to restart by shutting it off, as alt+f1, ctl+alt+bksp etc. don't work. 

How do I start troubleshooting this?  I don't think I'm running anything unusual.  Today I had firefox with a couple of tabs, thunderbird, and kile open, then I tried to start openoffice and it really tanked.

---

### Post by ago on 2008-06-26
look at dmesg and the logs, and some monitoring program to find the bottleneck. See the sysctl key combinations if the keyboard becomes unresponsible

---

