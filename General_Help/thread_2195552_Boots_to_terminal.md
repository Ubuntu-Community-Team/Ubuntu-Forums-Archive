---
title: "Boots to terminal"
date: 2013-12-24
forum: General Help
---

### Post by jason13 on 2013-12-24
My desktop locked up in the middle of a session and now it's just booting to a terminal interface, apparently networking works. How should I go about diagnosing it?

---

### Post by jason13 on 2013-12-24
Tried booting again. Just before the CL screen the splash screen flashes very fast. the first thing it says is Cannot write bytes: broken pipe, then it runs through a few other lines about CUPS.

---

### Post by egeezer on 2013-12-24
What happens when you login at the terminal prompt and run the command "startx" (with no quotes?

(It might have to be sudo startx)

---

### Post by jason13 on 2013-12-25
results as follows

```
NVIDIA: API mismatch: the NVIDIA kernel module ahs version 304.88, but this NVIDIA driver component has version 304.108. Please make sure that the kernel module and all NVIDIA river components have the same version.

Fatal server error:
no screens found
(EE)
...

server terminated with error (1). Closing log file
...
xinit: unable to connect to X server: No such file or directory
```

ellipsis are mine to shorten extraneous information

This tells me something is wrong with the X window system; in my experience things have gone wrong with X on my system in the past where the fix is to do nothing, and eventually I'll get lucky with a reboot and everything will be fine, for a time. However if this is a previously documented error I'm sure I am capable of repairing it with help.

---

