---
title: "Which desktop am I running?"
date: 2013-04-14
forum: General Help
---

### Post by mringer on 2013-04-14
Running Lubuntu 12.04 off the Live CD, nearly all offered updates (some failed).
 I would like to know which desktop I am running. 

Searching UB forums, I found nothing relevant.

Searching Google, I found:

```

# echo $DESKTOP_SESSION  
```

This prints a blank line.  Also:

```

# wmctrl -d
0  * DG: 1280x800  VP: 0,0  WA: 0,0 1280x776  desktop 1
1  - DG: 1280x800  VP: 0,0  WA: 0,0 1280x776  desktop 2
```

I suspect that  wmctrl   is unsuitable for this purpose. Please, what should I do?
Thank you

---

### Post by ibjsb4 on 2013-04-14
Its:

```
echo $DESKTOP_SESSION
```

---

### Post by efflandt on 2013-04-14
You probably should not try to update a Live CD or install things like video drivers (even when you use Startup Disk Creator to boot it from USB with persistent data), because initial boot is from a fixed squashfs file system (before casper-rw with persistent data is mounted, if you have persistent data). You can install programs that run after booting, but if you do not have working persistent data (or booted from a CD), those will disappear when you shut down.

I don't know if I have a Lubuntu live/install system handy, but on a 12.04 Lubuntu installed system these are some of the variables that **env** command returns:

XDG_MENU_PREFIX=lxde-
DESKTOP_SESSION=Lubuntu
GDMSESSION=Lubuntu (even though it uses lightdm, not gdm)
XDG_CURRENT_DESKTOP=LXDE

To see what is actually running you can scroll through: **ps aux | less**

---

