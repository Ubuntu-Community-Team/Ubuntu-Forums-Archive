---
title: "[SOLVED] Which session type will not have compiz fusion? Failsafe GNOME?"
date: 2007-12-24
forum: General Help
---

### Post by rainwalker on 2007-12-24
I need to start a session without Compiz Fusion enabled, because it's crashing my comp every time I log in (trying to enable blur effects). Which session type (choosing from the login screen) will not have it enabled?

---

### Post by ~LoKe on 2007-12-24
Failsafe Gnome shouldn't load compiz.  How did you set up compiz to run?  Is it a session application?

---

### Post by ~LoKe on 2007-12-24
Hm...or you could always edit /etc/X11/xorg.conf and change "nvidia" to "nv" for your driver.  This will revert back to the old driver which won't allow compiz to run, allowing you to log in and change things as you see fit.  Afterwards, change the driver back.

I imagine there's a more elegant solution, though...

---

### Post by rainwalker on 2007-12-24
Failsafe GNOME didn't load it, and I think I fixed my problem.

Compiz is technically a session application, but it's set to enable by itself if your hardware supports it, it's not in the Sessions window

Oh and I'm using ATI, but thanks for the suggestion :)

---

