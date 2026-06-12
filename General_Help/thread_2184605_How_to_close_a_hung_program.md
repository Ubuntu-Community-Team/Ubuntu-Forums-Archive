---
title: "How to close a hung program?"
date: 2013-10-29
forum: General Help
---

### Post by Vannyi on 2013-10-29
XBMC just hung on me and if I try and close it using the X in the top left corner or by right clicking the icon and selecting quit in the Ubuntu 12.04 launcher, nothing happens.

With Windows, you can bring up task manager and try and close it that way.

Is there an equivalent option in Ubuntu or is a reboot the only solution when this occurs?

---

### Post by PeterRJG on 2013-10-29
You could do Ctrl+Alt+F1, log in and kill the process that way. Ctrl+Alt+F7 (or maybe F8) will get you back to your current X session. If F7 doesn't do it, try F8.

---

### Post by nativehound on 2013-10-29
You could use "System Monitor", it's similar to "Task Manager". Just right click the process and kill it.

---

### Post by oldos2er on 2013-10-30
I use *xkill*.

---

### Post by tgalati4 on 2013-10-30
```
sudo killall xbmc
sudo kill -9 6578
```

Substitue 6578 with the actual process idenification number (PID).
Look at the log files to see what actually hung so that you don't have to shut down the system in such a brute force fashion.

There are several "Force Quit" panel applets for different desktop environments.

---

### Post by Redalien0304 on 2013-10-30
System Monitor is what i use to kill a unresponsive program

---

