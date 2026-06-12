---
title: "disabling ctrl-alt-plus / ctrl-alt-minus"
date: 2008-02-11
forum: General Help
---

### Post by descentspb on 2008-02-11
Is there a way to disable this keys or just to move the resolution change to other shortcuts?

I've installed photoshop through wine and it really annoys me when i want to zoom in or out, but instead after the pressing of this keys my system becomes almost absolutely unresponsive!

---

### Post by pointone on 2008-02-11
[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html#sect4](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html#sect4)

The "DontZoom" xorg.conf option is what you're looking for.

---

### Post by descentspb on 2008-02-12
thanks a lot, mate!

---

### Post by krejzihors on 2008-05-21
i have exactly the opposite problem. i want to zoom through available resolutions, but ctrl-alt-plus does not work. i put "DontZoom" to "false" in xorg.conf, but it did nothing. i have lenovo R60e laptop with 15'' 1024x768 screen and intel 945 graphic card.

---

