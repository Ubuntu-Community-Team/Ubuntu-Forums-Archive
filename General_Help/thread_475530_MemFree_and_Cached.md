---
title: "MemFree and Cached"
date: 2007-06-16
forum: General Help
---

### Post by Dr Eigen on 2007-06-16
Hi folks

Can someone please confirm something for me:  In a healthy running system, it's a good thing to have /proc/meminfo showing small MemFree... that indicates disk caching is working properly?

In other words, on a system that's been up a month, with 30-odd users logged in and working, the following is bad if it persists...

$ cat /proc/meminfo | head -7
MemTotal:      8162580 kB
MemFree:       6352020 kB
Buffers:         37928 kB
Cached:        1502268 kB
SwapCached:      12720 kB
Active:         213540 kB
Inactive:      1435680 kB


(I don't like to think of myself as a noob, having been running on linux systems for the better part of a decade, but this is something I haven't had to deal with before...)

---

