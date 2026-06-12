---
title: "System Lag"
date: 2024-10-12
forum: General Help
---

### Post by bmcclint2 on 2024-10-12
This post kind of went off the rails.  I started searching today for this exact thing.  It seems to be somewhat common as there are other posts about it.  My 22.04 -> 24.04 is experiencing the same type of behavior.  Things are just laggy.  Anything UI related it seems.  Not sure whats going on or if others have found solution(s).  I kept a 22.04 system BU and about to revert.  Not sure if the problem is IO or UI related.  Things like the file browser and Handbrake, VSCode, etc. are laggy...dialogs and the like.  Things just open slow.  Using terminal for example, opening a second tab and trying to detach tab 2 crashes terminal all together.  Something is off.  Not sure what...constructive thoughts appreciated...

---

### Post by ian-weisser on 2024-10-12
Review your logs. Check "top". Check "free". Look for unusual network activity.

Maybe it's a misconfiguration. Maybe you're out of RAM (swapping). Maybe your hard drive is dying. Maybe you picked up a cryptominer or other malware. Many possibilities.

See if you can duplicate the lag using a LiveUSB's "Try Ubuntu" environment.

---

### Post by Monster_user on 2024-10-13
I just upgraded to Kubuntu 24.04 LTS. My system is also lagging. 

The KDE plasma-systemmonitor is showing 100% CPU utilization on "Core 1", and 0% utilization on the rest of my cores on an 11th Gen Intel Core i7-1165G7, on the "History" tab. "uname -a" reports a kernel with SMP in the name, am I running into some core 1 "affinity" glitch?

Most of that 100% CPU was used by my web browser with certain tabs/websites open, no indication of any malware on the system.

---

