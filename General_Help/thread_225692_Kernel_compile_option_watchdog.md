---
title: "Kernel compile option: watchdog"
date: 2006-07-30
forum: General Help
---

### Post by immesys on 2006-07-30
My pc keeps crashing ever 14 or so hours, but I don't really care why (its really dodge anyway). I'm using it as a web server so I want it to reset itself when it crashes.

I don't have a hardware watchdog card but I've been told that some of the newer kernels can be compiled with a software watchdog kind of thing.

I'm about to follow the Kernel recompile sticky thread but I want to know when in the process I must specify watchdog support when I'm compiling it. Can anyone tell me?

Thanks for the help.

---

### Post by caserio on 2006-07-30
Hi,

Watchdog cards support is already compiled as modules on your system. See /boot/config <*your_kernel*> for details (Section -> # Watchdog Cards).

---

### Post by immesys on 2006-07-30
thanks, I've gone and compiled a new kernel with "Software Watchdog" (Device Drivers->character devices or something similar) on already (as a builtin as opposed to module).

My new kernel appears to work ok. Now I don't know how to configure watchdog correctly. I've set it all up in /etc/watchdog.conf but if the conditions aren't met it still doesn't reboot my pc. What else must be done?

---

