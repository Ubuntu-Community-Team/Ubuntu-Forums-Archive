---
title: "Too many HDMI devices"
date: 2013-10-24
forum: General Help
---

### Post by Pierre_duParte on 2013-10-24
I have been struggling to get sound over HDMI on an existing (myth)Ubuntu install with recently upgraded (MOBO) hardware.

 Out of frustration I did a clean install to an alternative hard disk. Sound over HDMI worked fine once I ran fglrx-updates.

Reverting to the original existing Ubuntu installation, I did 
```
 dmesg | grep HDMI
```

It returned eight instances of 
```
Too many HDMI devices
```

Can someone tell to me what this means? Is it, as I suspect, the cause for no sound over HDMI? And if so, is there anything I can do to short of a new install to fix the problem, assuming it is one?

Thanks

Pierre

---

