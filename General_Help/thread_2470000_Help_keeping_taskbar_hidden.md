---
title: "Help keeping taskbar hidden"
date: 2021-12-16
forum: General Help
---

### Post by wrybread on 2021-12-16
I'm using Lubuntu in a kiosk environment, and I have the taskbar set to auto hide. But sometimes when changing windows the taskbar still appears at the bottom of the screen.

I've tried doing workarounds like have a script put focus on another window (using both wmctrl and xdotool), which works, but it still casues the taskbar to appear for a split second, which doesn't look good on a kiosk.

My taskbar is LXPanel 0.9.3, my desktop environment is LXDE.

I don't imagine there's some way to hide the taskbar and keep it hidden until I need it? Maybe that I can run from a script?

Or maybe some other desktop environment that wouldn't have this problem?

Full output from screenfetch is:

```
OS: Ubuntu 18.04 bionic
Kernel: x86_64 Linux 4.15.0-147-generic
Shell: bash 4.4.20
DE: LXDE lxpanel 0.9.3
WM: OpenBox
GTK Theme: Lubuntu-default [GTK2]
Icon Theme: Lubuntu
Font: Ubuntu 11
CPU: Intel Core i5-4690 @ 4x 3.9GHz [27.8°C]
GPU: NVA5
RAM: 923MiB / 15964MiB

```

---

### Post by wrybread on 2021-12-17
Well at least I figured out why the taskbar was appearing: it's because one of the scripts is changing the screen resolution, which then leaves the mouse at the bottom of the screen, which then makes the taskbar appear (since I have the taskbar set to autohide).

So the taskbar is doing exactly what it's supposed to do. Which means I guess it's solved.

Still, if anyone happens to know some command I can fire that will hide the taskbar, I'd be interested.

---

### Post by TheFu on 2021-12-17
Don't let any panel run.  In older LXDE setups, the panel was part of the DE startup, but could easily be removed.  For added safety, remove execute permissions from lxpanel.  Check to see that it doesn't autospawn over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over.  If you don't want a DE, don't use one.

---

