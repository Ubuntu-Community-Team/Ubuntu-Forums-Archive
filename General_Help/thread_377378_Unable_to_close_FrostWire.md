---
title: "Unable to close FrostWire"
date: 2007-03-06
forum: General Help
---

### Post by vnt87 on 2007-03-06
I just installed FrostWire on my Edgy using the deb package downloaded from their homepage. It runs just fine and there're no problems except that I was unable to terminate it. I tried clicking the "X", tried going to File>Close, tried right clicking on the taskbar and select "close" but all it did to FrostWire was simply minimizing the FrostWire windows. Right now I had to move the FrostWire window to a different workspace. I wonder if there's a trick to close this prog that I don't know of?

---

### Post by taurus on 2007-03-06
If you know the PID (process ID), you can kill it.  To figure out what the PID is, run this command from a terminal and look at the value on the first column.

```
ps -A
```
Assuming it has a value of 1234 (for frostwire), kill it with

```
sudo kill -9 1234
```

---

### Post by vnt87 on 2007-03-06
OK I got it to close now. Seems like it won't close as long as you still have some items in your download queue (regardless of whether they're complete or not, as all of my downloads were done). So I had to go to Frostwire options>System Tray and choose 'shut down immediately'.
It doesn't look like the 'system tray' feature doesn't work properly in this version (4.13.1) either, since I have never seen it minimize to the tray like Limewire.

PS. Thanks for that info Taurus, although I do not need it to close frostwire now, but that info will definitely comes in handy the next time I run into a stuborn program. I hope Ubuntu has some sort of task manager gui like the one in Windows though, it's easier to control the running processes.

---

### Post by amphet on 2007-03-06
you can use 'xkill' to terminate non responsive programs as well

---

### Post by garythornton1956 on 2008-03-26
Version 4.13.5 on Gutsy also does not display any option to minimise to system tray.

---

### Post by markharding557 on 2008-03-26
you can terminate a process in the system monitor

---

