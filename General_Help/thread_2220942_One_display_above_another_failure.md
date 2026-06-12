---
title: "One display above another failure"
date: 2014-04-30
forum: General Help
---

### Post by KeremE on 2014-04-30
After upgrading from Ubuntu 12.04 to Ubuntu 14.04 with GNOME 3.10.4, I am no longer able to use multiple displays in the configuration shown in the following screenshot (secondary display directly above my primary display). As shown in the screenshot, a "maximized" window in the secondary display is squished, with its left edge starting at the right edge of the primary display. This is not a problem I had using the gnome-classic mode in 12.04 and the gnome-flashback mode in 14.04 (which failed for other reasons).

Does anyone know why this is happening and how to fix it?

Thank you very much!

[ATTACH=CONFIG]252658[/ATTACH]

---

### Post by Bucky Ball on 2014-04-30
I use arandr to get my monitors working (I have them set up with one above the other also). It's in the repositories.

I found it to work where other things have failed. Good luck.

---

### Post by KeremE on 2014-04-30
Thanks for your response, I installed arandr, but the same problem persists.

EDIT: I edited the layout script to make my secondary (top) monitor my primary monitor, and it now seems to work - the problem only happens when there is a secondary monitor on top of my primary monitor. Thanks for all of your help!

---

