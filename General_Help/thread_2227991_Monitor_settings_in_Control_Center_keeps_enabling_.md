---
title: "Monitor settings in Control Center keeps enabling panning!"
date: 2014-06-05
forum: General Help
---

### Post by icest0rm on 2014-06-05
Hi,
I have a laptop with two cards (nvidia 4200M and integrated Intel) and 3 monitor setup (DP-0 and DP-1 connected to Nvidia card and VGA-1-0 connected to Intel) using drivers nvidia-331 and nvidia-prime.
All was working well, since a day after undocking/docking the laptop, dunno if I did some updates, but cannot get anymore those 3 monitors to act indipendently as if they were alone.
DP-0 and DP-1 keeps panning and I can't find a way to disable it.

I enable the 3 monitors using Ubuntu monitor settings in Control Center, disable duplication and set the three monitors one after the other, but this is what xrandr output shows:

```

nbr@nbr-nb:~$ xrandr -q|grep conn
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 disconnected (normal left inverted right x axis y axis)
DP-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm **panning 2560x1024+0+0 tracking 4240x1050+0+0** border 0/0/0/0
DP-1 connected primary 1680x1050+1280+0 (normal left inverted right x axis y axis) 433mm x 270mm **panning 2960x1050+1280+0 tracking 4240x1050+0+0** border 0/0/0/0
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
LVDS-1-0 connected
VGA-1-0 connected 1280x1024+2960+0 376mm x 301mm
nbr@nbr-nb:~$ 

```

as you can see those 2 monitors are panning...

I tried to specify with xrandr the parameter --panning 0x0+0+0 for both monitors to disable it but this won't work (configuring monitors with xrandr do also worse things, like duplicating DP-0 and DP-1).

Hope someone has a hint...all was working well apart some troubles when I undocked/docked the laptop, but this would solve with reboot. Now since that day I had this issue, I cannot revert back to working config anymore...

Thanks

---

### Post by icest0rm on 2014-06-10
no-one?

---

