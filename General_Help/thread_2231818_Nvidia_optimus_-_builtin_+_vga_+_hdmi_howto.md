---
title: "Nvidia optimus - builtin + vga + hdmi howto"
date: 2014-06-28
forum: General Help
---

### Post by alfredo.marchini on 2014-06-28
Hi all,
I decided to write this 3d because it's many time I try to connect my 2 dell 24'' monitors to my laptop asus n56vz, I have some tuning to do and I would like to know if someone adopted my solution.
The laptop has a Nvidia GeForce GT 650M, with Optimus support.
The os is gnome-ubuntu 14.04 LTS amd64, but I think it works also on other platforms, as DisplayManager I use GDM, but it works also with lightdm.
I found many guides on internet, but I didn't found anything that permit me to reach this result.

How it works:
Phase 1: laptop without any external monitor connected, I attach VGA monitor and everythings works well (Obviously because VGA is connected to Intel Chipset).
Phase 2: without doing anything I connect the HDMI port with the second monitor. Result: the monitor is recognized, I need only to configure the position inside virtual screen.

this is what's happen in windows enviroment with original drivers.
To make this work It was more simple than many howto I find on internet: 

1) Add ppa xorg-edgers
2) Install nvidia-persistenced with nvidia-opencl-icd-340.

It's not already perfect, there are anyway some problems, for example you are using nouveau drivers and not nvidia official drivers.
Another problem is the hdmi monitor that sometimes has refreshing problems.
If anyone has suggestions, better configuration or else I will be very happy to know...
Bye

---

