---
title: "Locking screen when closing lid on laptop"
date: 2008-03-01
forum: General Help
---

### Post by TC10284 on 2008-03-01
Hey all,

I am running Gutsy on a T43p laptop. For security, I would like Ubuntu to lock the system when I close the lid on my laptop. Is there a way that I can do this? I have selected "Lock screen when screensaver is active" in the Screensaver options, but the screen isn't locked when I open the lid.

---

### Post by le1 on 2008-04-02
It's easy to do it:

Alt + F2
next:
gconf-editor
next:
apps --> gnome-power-manager --> lock
next:
check in value on blank_screen

done.

have a great day.

---

