---
title: "Tried to install a new wifi card. Rebooted and now PC running in software rendering"
date: 2023-07-13
forum: General Help
---

### Post by dorlow on 2023-07-13
Ok, not sure where I went wrong. I downloaded a script from the wifi adapter manufacturer. Ran it. It failed. So, then I ran an apt-get update and apt-get upgrade. I can't figure out what I did but one thing had me type a password that I was supposed to reboot and have to type that password again. When I rebooted, it never asked for the password it said it was going to ask for.


I started the computer back up and now it's stuck in software rendering mode. I don't have any restore points.... ooops.

---

### Post by TheFu on 2023-07-13
Always pick hardware for Linux that doesn't require external drivers.  You want drivers to be part of the kernel. No download or extra install needed, unless you prefer to be challenged.  Some people like that.

---

### Post by dorlow on 2023-07-13
Well, I got my video back.  I switched to the wayland driver.  I'm not sure if I was using that before.  I downloaded Timeline this time and made a restore point before I start tinkering again.

---

### Post by TheFu on 2023-07-13
> **dorlow said:**
> Well, I got my video back.  I switched to the wayland driver.  I'm not sure if I was using that before.  I downloaded Timeline this time and made a restore point before I start tinkering again.

Backups are always a good thing. At least weekly, if not daily.  I've never heard of Timeline before. Hope it works as you need. [https://snapcraft.io/timeline](https://snapcraft.io/timeline) makes me think you have the wrong software. Looks like "Timeline" is for creating Gantt charts, which is something a project manager would use. [https://en.wikipedia.org/wiki/File:GanttChartAnatomy.svg](https://en.wikipedia.org/wiki/File:GanttChartAnatomy.svg)

Perhaps you meant Timeshift?  Timeshift is very popular and especially suited for systems using BTRFS.  Without BTRFS, it becomes a fancy rsync tool, which is fine.

---

