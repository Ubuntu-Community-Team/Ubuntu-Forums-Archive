---
title: "Primary monitor only works when secondary is connected"
date: 2017-09-26
forum: General Help
---

### Post by princeless on 2017-09-26
Hi, 

I have Kubuntu 14.05.5 running on a Sony Vaio notebook. 

When no external monitor is connected, the internal monitor (=primary display) is not showing anything. 
When I connect an external VGA monitor, the internal one works as specified in the "Display" settings. 
(In the Display settings, the internal monitor is set as primary display, the external display is set to inactive.)

Similarly, "xrandr -q" reports 2 monitors to be connected when both are connected, and the internal one being primary. 
When I run "xrandr -q" while the external monitor is disconnected, only the internal one is recognized (not specified to be primary).

I tried "xrandr --output LVDS1 --primary" but that didn't change anything. 

It is my friend's computer. They reported that the problem first occurred after installing updates while an external monitor was connected. 

What to do?

---

