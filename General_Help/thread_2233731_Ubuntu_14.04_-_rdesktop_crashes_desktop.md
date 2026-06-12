---
title: "Ubuntu 14.04 - rdesktop crashes desktop"
date: 2014-07-10
forum: General Help
---

### Post by jeroenclaeys on 2014-07-10
Hi all


For a few weeks I've been experiencing crashes when RDP'ing using rdesktop from Ubuntu 14.04 to Windows Server 2008 R2. When having an RDP connection open my desktop session will quit and I'm presented with a console screen stating "Restoring resolver state". Sometimes my desktop is restored and a login screen is shown, other times I have to go to one of the console screens and reboot my OS.


- The crash doesn't occur every time, nor does it happen at the same intervals.
- It occurs only when using rdesktop.
- I'm working on a Latitude E6540 with AMD Radeon graphics card, using the open source driver.
- The following syslog entry seems relevant: "gnome-session[6209]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012" 


Has anyone else encountered this problem?

---

