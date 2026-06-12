---
title: "Unnattended OS update problem after changing some config files"
date: 2016-11-12
forum: General Help
---

### Post by CrewDK on 2016-11-12
I run Ubuntu 16.04.1. I want to increase resolution of grub menu so I added into my /etc/default/grub this line: 

```
GRUB_GFXMODE=1152x864x32
```

It works fine, until I trying to run unattended system upgrade. Every time I running upgrade it stacks with "Configuring grub-pc" console window and it wants to turn back my changes with /etc/default/grub. 

[ATTACH=CONFIG]272104[/ATTACH][ATTACH=CONFIG]272105[/ATTACH]

What I did wrong? How can I prevent upgrade from interrupting or from changing back my configs?

---

### Post by wildmanne39 on 2016-11-12
*Thread moved to **General Help**.*

---

