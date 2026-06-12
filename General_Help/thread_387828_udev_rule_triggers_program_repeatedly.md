---
title: "udev rule triggers program repeatedly"
date: 2007-03-18
forum: General Help
---

### Post by yoink23 on 2007-03-18
I'm trying to set up a udev rule so that when my usb flash drive is plugged in a program is run.  Unfortunately, when I use this rule...

```
DRIVERS=="usb", ATTRS{serial}=="0C80AC6022D1E8DA", RUN+="/usr/local/bin/usb-events.sh" 
```

...it seems to trigger the script somewhere around 15 times.  

Does anyone have experience with this problem?

BTW, my system is running feisty and is updated.  

TIA,
Yoink

---

