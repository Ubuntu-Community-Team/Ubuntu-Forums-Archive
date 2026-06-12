---
title: "cat /proc/bus/input/devices -- No IR device listed"
date: 2006-11-19
forum: General Help
---

### Post by daveyiv on 2006-11-19
When I run cat /proc/bus/input/devices my IR device is not listed (WinTV PVR-150). However when I ran the mode2 -d /dev/lirc0 command, it is able to see the input from the remote, however irw is not able to see any input. Anyone know what the heck is going on?

---

### Post by thirstycat on 2006-11-20
well, for what it's worth, you've described my situation as well.

if you do a ```
 modprobe lirc_i2c;dmesg | grep lirc 
```

what do you get?

my logs show:
```
[17234941.012000] lirc_dev: IR Remote Control driver registered, at major 61
[17234941.016000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.

```

---

