---
title: "X/gdm crashes on suspend"
date: 2007-11-06
forum: General Help
---

### Post by relix on 2007-11-06
When I put my PC in suspend, everything's going great. When I make it come back, however, I'm at the main loginscreen of the gdm. Not, like one would expect, at the "locked screen"-login. This means my session is gone and any apps that were open got shut down.

I checked the log files and it looks like X/gdm is getting a signal 11 which makes it shutdown.

Can anyone point me in the right direction on how to solve this? My current system specs are Gutsy + Nvidia (proprietary drivers). Suspend worked fine using dapper/edgy/feisty + Ati (proprietary drivers; I switched vga cards and installed gutsy from scratch at the same time).

---

