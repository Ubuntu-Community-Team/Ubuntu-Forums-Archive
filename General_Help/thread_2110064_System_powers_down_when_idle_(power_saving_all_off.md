---
title: "System powers down when idle (power saving all off)"
date: 2013-01-29
forum: General Help
---

### Post by StuartPM on 2013-01-29
Hi all,

I'm running Ubuntu 12.04 on an old laptop as my XBMC machine / media server. I'm using KDE and switched off all power saving except hibernate on very low battery (It's plugged in all of the time anyway). I then added XBMC as a gnome replacement and changed settings to boot directly to XBMC. I can exit XBMC and log into KDE at anytime.

Anyway, when the machine has been idle for a while (around 30 mins) it powers down. If I switch back to KDE all of the power saving options are still off and even if I'm in XBMC mode and I SSH with -X and run the power control panel remotely, it still shows all power saving options are off.

I can't seem to see anything in the logs as to why it's shutting down. I originally thought it may be shutting down due to overheating, but I can use it for hours to watch videos and it's fine. I've not yet checked to see if it shuts down from KDE when idle.

I've tried acpi=off as a kernel option in GRUB but it prevents the system from booting.

Does anyone know if there is another reason for a shutdown to occur? Where would I find logs on what made it shut down? The log's I've looked through dont' show anything happening at the time it powers down.

Thanks,
Stu

---

