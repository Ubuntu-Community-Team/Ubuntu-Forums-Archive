---
title: "Chrome hanging on resume from suspend"
date: 2022-12-18
forum: General Help
---

### Post by sorceror171 on 2022-12-18
Apparently this was happening a while back, but it's new on my system (about a week?) and 100% reproducible. Every time I suspend my desktop, once I resume Chrome is locked up. The windows are there, but don't update. When I scroll to that desktop, there are scraps of whatever was on the previous desktop instead of the Chrome windows.

If I run the command ```
pkill -f 'chrome \-\-type=gpu-process'
``` the desktop locks up for a second or two but Chrome comes back and the system responds again. Firefox does not display this behavior; it resumes from suspend just fine.

(A search on 'Chrome hang' and 'Chrome gpu-process' didn't turn up anything recent here...)

Xubuntu 22.04
AMD Ryzen 9 3950X
64GB RAM
ASUS Crosshair VIII Hero (WI-FI)
Nvidia 2080 Super
Nvidia driver version 525.60.11.

---

