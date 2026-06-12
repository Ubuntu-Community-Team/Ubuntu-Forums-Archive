---
title: "[SOLVED] how to kill uninteruptable process?"
date: 2008-03-16
forum: General Help
---

### Post by ogcub on 2008-03-16
I had strange totem-gstreamer crash. It simply disappeared. however process was left in the interruptable state eating all the cpu. I tried kill, killall, sudo kill, gnome-system-monitor but nothing helped. I tried to restart Xorg but with no avail. finally I restarted my PC, however it hanged. I had to resort to Sysrq keys to restart it. 

How to kill such processes?

---

### Post by scragar on 2008-03-16
```
kill -9 **PID**
```
or:
```
killall -9 totem-gstreamer
```

the -9 is interchangeable with -kill if you want to type a little more

---

### Post by Oldsoldier2003 on 2008-03-16
> **scragar said:**
> ```
kill -9 **PID**
```
or:
```
killall -9 totem-gstreamer
```

the -9 is interchangeable with -kill if you want to type a little more

+1 for kill -9

---

### Post by ogcub on 2008-03-17
Thanks, didn't know that.

---

### Post by BlueSkyNIS on 2008-05-17
Didn't work for me :(

[http://ubuntuforums.org/showthread.php?t=795603]("http://ubuntuforums.org/showthread.php?t=795603")

---

