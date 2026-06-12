---
title: "Ubuntu Studio randomly hangs on logon screen"
date: 2022-02-06
forum: General Help
---

### Post by s-bartos on 2022-02-06
I've been running Ubuntu Studio for about a year and from the start I have had a persistent problem with the Plasma logon screen, which randomly hangs, the mouse works (moves) but none of the screen controls respond, the password can't be entered. The only workaround I'v discovered is to CTRL-ALT-F4 to the console, logon and run:

sudo systemctl restart sddm.service

This reloads the logn screen which then works. I probably have to do this for about 25% of logons from boot. I have no other system issues, once in and running everything works flawlessly.

Some system specs:

Operating System: Ubuntu Studio 21.10
KDE Plasma Version: 5.22.5
KDE Frameworks Version: 5.86.0
Qt Version: 5.15.2
Kernel Version: 5.13.0-28-lowlatency (64-bit)
Graphics Platform: X11
Processors: 12 × AMD Ryzen 5 3600 6-Core Processor
Memory: 15.5 GiB of RAM
Graphics Processor: NVIDIA GeForce GTX 750 Ti/PCIe/SSE2

I run updates as soon as they are presented, so the system is fully patched.

Anyone know if there's a fix for this as its somewhat irritating and has been persistent from day one.

---

