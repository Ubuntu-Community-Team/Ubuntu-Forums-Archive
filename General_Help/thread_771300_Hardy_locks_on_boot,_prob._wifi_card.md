---
title: "Hardy locks on boot, prob. wifi card"
date: 2008-04-27
forum: General Help
---

### Post by anandus on 2008-04-27
I used 7.10 without any problems.
And then I upgraded to Hardy, but it hung on boot.

When I remove my wifi card it installs and boots fine. When I boot with the wificard inserted it hangs.

To be sure I did a clean install, same issue.

It hangs, just after loading the broadcom drivers, around the 'root system'/'activate swap' area, but I'm certain it's the wifi-card, because without it, it's fine.

The wifi-card's chip is broadcom 4306.

So what do I do? Reinstall 7.10, or is there a solution to this problem?

---

### Post by anandus on 2008-04-28
No-one? :(

---

### Post by Mr Frosti on 2008-04-28
Broadcom does not offer native Linux drivers, nor access to their hardware specs / driver implementation codebase. As a result, Broadcom support is emulated using the "ndiswrapper". Since your machine is freezing, this wrapper is where I suspect the breaking point is. 

If you boot your machine without the wireless card inserted, look at your system log files. There is a GUI for this under "System -> Administration -> View Logs". Specifically, look under "kern.log", "messages", and "syslog" and their most recent entries. Do you see any error information?

Does the Broadcom wireless card work if it is inserted after the machine has booted? Insert the card while already booted, and watch these log files for new entries (they will be bold). See if the new entries indicate any errors.

---

