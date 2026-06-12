---
title: "Unintended/unexpected wake-up from suspend mode"
date: 2014-08-26
forum: General Help
---

### Post by go3d on 2014-08-26
I have a strange problem with my notebook. Sometimes, when in suspend (to RAM) mode, the system wakes up on its own, completely unintended. This has happened even if the notebook rests on a table with closed lid, no movement or vibration whatsoever (so no unnoticed key-press in a bag or the like). Also, there is nothing attached to it, like any USB device that could cause this behavior.
I use it almost daily and the mysterious wake-ups happen like 3 times a week.

I have analyzed some log files (syslog, pm-suspend, daemon.log, etc) but I couldn't find any useful information other than the time at which the wake-up happened. It is certainly not a BIOS thing, I've checked that. Besides, the times at which it happens are random.

Any ideas how I could pin point the cause of this problem? My system:
Model: Acer V5-573G
Debian: Wheezy 7.5
DesktopEnv: KDE 4.12.4
Kernel: 3.13-1-686-pae #1 SMP Debian 3.13.10-1

I know it is Debian and not Ubuntu, but since Ubuntu is based on Debian, I assume the problem could be relevant to Ubuntu users as well.

Regards
Go3d

---

