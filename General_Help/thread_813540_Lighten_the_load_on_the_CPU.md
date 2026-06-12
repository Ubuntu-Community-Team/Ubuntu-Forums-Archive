---
title: "Lighten the load on the CPU?"
date: 2008-05-30
forum: General Help
---

### Post by Mayur on 2008-05-30
Are there any unneeded processes that can be removed and if so how?  I have a really slow CPU and I really just use ubuntu to browse the net and IM.

AMD Duron 892 MHz
~500Mb Ram
nVidia GeForve FX 5200 128Mb Video Card

---

### Post by wolfen69 on 2008-05-30
go to system>admin>services and uncheck what you dont need. if all you do is surf and IM, you may want to consider Flubuntu or at most, Xubuntu. they are lighter and slightly faster.

---

### Post by Mayur on 2008-05-30
Is it possible to use xubuntu but still get the ubuntu feel, color wise and what not?

---

### Post by kerry_s on 2008-05-30
you call that slow, mines 450mhz 256mb ram, but i bet mine could slap yours up and down the street. :lolflag:

seriously, it really depends on how much your willing to give things up in the name of speed. switching to a window manager is a ton of a start, using lighter programs in place of the bigger stuff, will also give that fast filling.

you can try it on your current install, but a custom install is the best.
anyways open a terminal:

sudo apt-get install fluxbox menu
sudo update-menus

now log out and select fluxbox in the menu, then log back in.

fluxbox is the most common, but there are many window managers to choose from, i use jwm for mine.

---

### Post by kerry_s on 2008-05-30
> **Mayur said:**
> Is it possible to use xubuntu but still get the ubuntu feel, color wise and what not?

yes, just install it-> sudo apt-get install xubuntu-desktop
log out select xfce4

it probably won't help much xubuntu is as heavy as gnome.

---

### Post by alguin2 on 2008-05-30
Try running System->Preferences->Appearance 
- Go to "**Visual Effects**" tab
- Choose **None**

Also, can you run System->Administration->SystemMonitor to find out the CPU pig?


What does SystemMonitor (Resources Tab) say about CPU, Memory, and Swap use? This is a good tool for finding out the CPU bottlenecks.

Good luck.

---

### Post by Mayur on 2008-05-30
The CPU load sits around 30% with some spikes here and there.
Mmeory: 242.6Mb of 503.3Mb used (48.2%)
Swap: 376.0 Kb of 893.3Mb used (0%)

And there are no visual effects on.

---

