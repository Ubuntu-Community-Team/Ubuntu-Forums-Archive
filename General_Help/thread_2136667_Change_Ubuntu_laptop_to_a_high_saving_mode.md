---
title: "Change Ubuntu laptop to a high saving mode?"
date: 2013-04-18
forum: General Help
---

### Post by cpu2007 on 2013-04-18
I'm asking this question only because I know that it is possible to configure a lot of things when using linux based OS.

I'm wondering whether is possible to set the status of a laptop on some sort of super saving mode.

For example, sometime I leave my laptop on on uTorrent while I'm downloading some files; I do close the lid as this saves a lot of energy, plus I do also change the battery settng to saving mode (in w7). 
All this increase the battery running time but is it there anyway where I can stop all the resources and have like only uTorrent running and using just the few essential resources vital to the application?

Thanks

---

### Post by cortman on 2013-04-18
If you don't have any other programs running, the system typically won't be running any extra or unnecessary processes.

---

### Post by cpu2007 on 2013-04-18
yes but for example, raspberry pi consumes a lot less because of it's hardware and eventually I'll move everything to raspberry pi so that I can use uTorrent from it and save it into an external hdd. Meanwhile, I was wondering whether is possible to reduce the voltage of the system to put it on a high saving mode, e.g have the same voltage like pi or close to it.

---

### Post by 3rdalbum on 2013-04-18
Run Powertop to see what programs are waking up the CPU, and then you can kill them when you go to do torrenting.

The Raspberry Pi is so efficient because of its CPU design (ARM) and SoC, your laptop can't get anywhere near that. Also, the Pi is very slow compared to your laptop.

---

### Post by cortman on 2013-04-18
> **3rdalbum said:**
> 
The Raspberry Pi is so efficient because of its CPU design (ARM) and SoC, your laptop can't get anywhere near that. Also, the Pi is very slow compared to your laptop.

^This. The Pi has very low spec hardware, and typically low spec = low power consumption.

---

### Post by cpu2007 on 2013-04-18
No doubt about the fact that is low power but running something uTorrent on a powerful machine or on a pi won't make such a difference, or am I wrong?
considering downloading doesn't require much power and more power will not improve download/upload speed so being able to down clock a system would be a viable method. For example, if I'm not mistaken, is possible to down clock android phones and they will consume a lot less. 
I was thinking that maybe is possible to create profiles on laptops that allow you to choose a profile where you set the cpu and other hardware to a very low consumption mode.

I'll check the tool you've suggested and see whether it does make any difference.

---

