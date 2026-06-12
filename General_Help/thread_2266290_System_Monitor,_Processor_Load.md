---
title: "System Monitor, Processor Load"
date: 2015-02-21
forum: General Help
---

### Post by pmi2 on 2015-02-21
Is there some reason why system monitor might be using an excessive amount of processor time when running as the only open app on the desktop?  By excessive, I mean around 8~9%, compared to 1% on Linux Mint on the same hardware. (I am using the Load Indicator applet to compare processor load with and without system monitor running.

Ubuntu 14.04 LTS, Unity, all other desktop apps closed
gnome-system-monitor 3.8.2.1-2ubuntu1
indicator-multiload 0.3-0ubuntu1

To put this in perspective, playing a video in 720P resolution using MPlayer seems to take about as much processor time as System Monitor, whiich does not seem to make much sense.  (This is my first 14.04 install w. Unity)  Thanks.

---

### Post by kerry_s on 2015-02-21
i believe i saw a bug report on that being a kernel bug, when i was googling something i forget what.

---

### Post by grahammechanical on 2015-02-21
I also have System Load Indicator installed. It is a useful utility. But if I want to know how much CPU and memory resources a process is using I run top from the terminal. Or I install htop and run that from the terminal.

Comparing percentages between your machine and mine would be useless unless we have the same hardware. On my machine with an Intel Core Duo 2.4 GHz and 1 GB RAM System Monitor uses between 2% - 3% CPU and 4.6 % memory. I would guess that the percentage used should get less the more powerful the CPU is. Actually, there should come a point when there is very little CPU activity even if System Monitor is not the only application open.  

What window compositor does Linux Mint use? If it does not use Compiz, then I would expect different results when comparing whatever UI Linux Mint is using to the Unity UI.

Regards.

---

### Post by pmi2 on 2015-02-21
> **grahammechanical said:**
> I also have System Load Indicator installed. It is a useful utility. But if I want to know how much CPU and memory resources a process is using I run top from the terminal. Or I install htop and run that from the terminal.I may try that, and i know there are alternatives.  I think I have used top in the past, but i specifically wanted to use the default tools from the repositories to get used to 14.04 and unity.  System load indicator to system monitor with its graphic interface is one click, so that seemed like a natural way to go.

> **grahammechanical said:**
> Comparing percentages between your machine and mine would be useless  unless we have the same hardware. On my machine with an Intel Core Duo  2.4 GHz and 1 GB RAM System Monitor uses between 2% - 3% CPU and 4.6 %  memory. I would guess that the percentage used should get less the more  powerful the CPU is. Actually, there should come a point when there is  very little CPU activity even if System Monitor is not the only  application open. Agreed, is should, but in my case, NOT.  The machine in question is as follows: Intel Core i5-3550, 3.30GHz × 4, Intel DH67GD mobo, 8 GB RAM, 250GB WD SATAII.  (Not a good combination, I admit, but assembled from refurbed parts).  It is a dual boot with Linux Mint 17.1 "Rebecca", and I set it up specifically for testing, and for learning Unity.  Not great, but not shabby as far as processor speed goes.

System Monitor consumes about 1% when booted in Linux Mint, and almost ten times that much, 8~9% under Ubuntu/Unity!

Linux Mint/Cinnamon cannot possibly by THAT much more efficient - not being familiar with Ubuntu/Unity, I suspect some kind of installation error on my part... :(

---

### Post by pmi2 on 2015-02-21
> **kerry_s said:**
> i believe i saw a bug report on that being a kernel bug, when i was googling something i forget what.If you (or anyone else) can think of a reference or link, please post it...

---

