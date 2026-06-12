---
title: "Previously wokring Dell 7440 with Dual External Displays now mirror"
date: 2015-04-24
forum: General Help
---

### Post by jameq on 2015-04-24
Hi,

I'm on Ubuntu 12.04.5 LTS, on a Dell Latitude E7440 with Docking station plugging into 2 Dell 22" LCD displays via DVI. 

Previously I was seeing 1 Desktop spread across both Displays.  Today, it is mirroring the Displays. (And I can't switch it back)

Looking in Applications->System Tools-> System Settings->Displays,  it only shows one Display and its labelled "Laptop"

Running xrandr, I get:> 
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1680 x 1050, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 0mm x 0mm
   1680x1050       0.0* 


I did the normal update yesterday and also installed some dependencies for another package. (Looking at /var/log/dpkg.log lists several packages which were "installed", but when I attempted to remove some of them, X became unusable).

Anyone have any ideas on how to revert it, and get the working configuration restored? 

thanks
James

---

