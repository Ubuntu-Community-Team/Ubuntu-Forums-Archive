---
title: "Modules fail to load at start up"
date: 2007-04-06
forum: General Help
---

### Post by Strelock on 2007-04-06
Hi  all,

My built-in card reader requires the following modules:
[I]tifm_core
tifm_sd
tifm_7xx1[/I]
If I load them in the given order everything works just great. Now I've added them to /etc/modules and after restart I do not see them in lsmod, card reader doesn't work so I had to modprobe them again...

---

