---
title: "xwrits missing window edges in Xenial"
date: 2016-06-21
forum: General Help
---

### Post by Moses_Moore on 2016-06-21
This is regarding the package [xwrits]("http://packages.ubuntu.com/xenial/xwrits").  I am using XFCE4 in Xubuntu. 
Since the upgrade to xenial, the xwrits window no longer has a titlebar for moving or resizing.  There's no option in the xwrits man page for windowless / modal windows / frameless windows.

How do I use xwrits with a titlebar & window frame again, as it was in ubuntu 15.10 ?

---

### Post by ajgreeny on 2016-06-21
It sounds as if your window manager is not running for some reason when that application is used.

Use Alt+F2 and command **xfwm4** which should start it, and it should then continue to start after a reboot.

Have a look at /usr/share/doc/xwrits/README to see if that gives you any clues.

---

### Post by Moses_Moore on 2016-06-26
> **ajgreeny said:**
> It sounds as if your window manager is not running .... `**xfwm4`** which should start it

Nope that's not it.  xfwm4 is running.
```
xfwm4-Message: Another Window Manager (Xfwm4) is already running on screen :0.0
xfwm4-Message: To replace the current window manager, try "--replace"
```

When I run `xwrits typetype=0` to cause it to bring up a window immediately, it still doesn't have windowborders nor a titlebar.  This worked in Xubuntu 15.10, doesn't work in Xubuntu 16.04 , so I'm certain it's not something I changed.

---

