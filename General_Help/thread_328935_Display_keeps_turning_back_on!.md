---
title: "Display keeps turning back on!"
date: 2006-12-31
forum: General Help
---

### Post by hackel on 2006-12-31
I have a very frustrating problem.  Whenever I turn off my laptop display, it comes back on 15 seconds later.  Some process seems to be re-activating it or something.  Here are the details:

I use xscreensaver, set to turn my display off after 15 minutes.  This never happens.  I can also deactivate the screen using "xset dpms force off", which works right away, then after 15 seconds the backlight on the display comes back on (but it's still blank), and then eventually the screensaver comes on, and it soaks up my CPU and makes the thing run hot until I turn it off.  Needless to say, this is very annoying.  I've experienced the same problems with the dreaded gnome-screensaver.  gnome-power-manager is running, and it is set to put the display to slee when computer is inactive for 16 minutes (for some reason that is the lowest setting available!).  The laptop has a Radeon XPRESS 200M, however this was not a problem in the past and I have not needed radeontool or something similar to deactivate the display.  I've enabled laptop-mode in acpi-support.  I'm not sure what else to try so I can troubleshoot this.  Any advice would be most appreciated.

Ryan

---

