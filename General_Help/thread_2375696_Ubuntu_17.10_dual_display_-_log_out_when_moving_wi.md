---
title: "Ubuntu 17.10 dual display - log out when moving windows from one to another display"
date: 2017-10-26
forum: General Help
---

### Post by Stefan383 on 2017-10-26
Hi,

I just upgraded from Ubuntu 17.04 to Ubuntu 17.10. I noticed two things after the upgrade which forced me to rollback to my backed-up old 17.04:

1. In dual monitor setup (Laptop with intel vga /Lenovo L450/ + ext monitor) when I move window (for instance Nautilus) from one display to another, it sometimes crashes and login dialog is displayed. It is possible to reproduce the issue by grabbing nautilus window and move it very fast between the 2 displays (shaking it from one display to another).

2. The GUI is not so fluet as it was in 17.04. It is a bit jerky when I move windows and also it feels a bit laggy.

Is anybody experiencing the same problem?

I will test this also with a clean install of 17.10. I did not have clean install but I had some late beta version clean install and I am able to reproduce the problem (1) also there.

---

### Post by Stefan383 on 2017-10-27
I can confirm the same issue (1) is present with recently downloaded final version of Ubuntu 17.10 in live usb mode. When I repeat very fast moving of the window from one display to the other it will crash. It is more difficult to reproduce it with the live usb, but I succeeded 2 times to crash it. In my upgraded 17.04->17.10 it will crash much faster. That's a pitty. It seems it is worth waiting till 18.04 is released.

---

### Post by uc50_ic4more on 2017-11-03
This is happening to me constantly; at seemingly random points. Sometimes it is when I am dragging a window from one monitor to the other while at other times it is simply when double-clicking a file or immediately after a keystroke.

I am on a ThinkPad W510 and an external HDMI monitor. I am currently using the nouveau driver; having switched to it believing it may be a proprietary NVIDIA driver issue.

---

### Post by Stefan383 on 2017-11-04
I have intel integrated graphics so I doubt this is related to proprietary drivers as I use no proprietary one. I think I will not upgrade till 18.04 LTS is available.

---

### Post by spp58ca2 on 2017-11-06
There may be more going on than crashing when moving windows. I just did the upgrade and I get logged out every 2 minutes when do nothing. Going to have to reload 17.04, too much pain trying to debug a problem when you get logged out every 2 minutes.

---

### Post by uc50_ic4more on 2017-11-08
Update: I have begun using the NVIDIA drivers and have not had this happen yet again. When moving a window - almost always a Chromium window, from my laptop monitor over to the HDMI, it seems as though the window manager is crashing and restarting: I lose my window borders across all windows for a minute.

---

