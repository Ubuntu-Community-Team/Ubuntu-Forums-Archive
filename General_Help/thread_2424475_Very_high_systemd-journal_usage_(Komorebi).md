---
title: "Very high systemd-journal usage (Komorebi)"
date: 2019-08-09
forum: General Help
---

### Post by smetca on 2019-08-09
I accidentally left my laptop running overnight and I come to find the fans going like crazy due to higher than normal cpu usage. Top showed that systemd-journal was using 100% on one of my cores. I checked journalctl and at around this time in the morning it showed this recurring issue starting [ATTACH]283762[/ATTACH]. Rebooting has fixed it for now, but I'm sure it will happen again.

I'm not familiar enough with Ubuntu to know what this means, but I assume some issue happened with the desktop wallpaper program I downloaded (Komorebi), I just have no idea what that issue is. If anyone could let me know how to avoid this in the future, I'd much appreciate it, and preferably without just uninstalling the software ;)

---

### Post by dino99 on 2019-08-10
Installing third party app like that one , is indeed at your own risk; Ubuntu does not know about it, and will not maintain it :confused:
Looks like its a buggy app: [https://github.com/cheesecakeufo/komorebi/issues](https://github.com/cheesecakeufo/komorebi/issues)

---

