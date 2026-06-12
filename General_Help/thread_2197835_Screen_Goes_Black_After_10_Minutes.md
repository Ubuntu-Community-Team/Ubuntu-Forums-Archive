---
title: "Screen Goes Black After 10 Minutes"
date: 2014-01-05
forum: General Help
---

### Post by robbiek01 on 2014-01-05
Hi all, I'm running lubuntu 13.10, and my screen keeps going black after 10 minutes.

I have tryed changing the settings manually, if I choose 0 never turn off or dim display, it still goes off in 10 minutes, if i choose to dim in 30 minutes same thing it dims in 10 minutes.

I have tryed running "xset s 0 0" from the command line, no joy.

I have tryed to Open Dconf-Editor Org -> Gnome -> Desktop -> Screensaver. In the window that appear, uncheck the line idle-activation-enabled and uncheck the line ubuntu-lock-on-suspend none of these work either

Regards

Robert

---

### Post by PopsTheSailor on 2014-01-05
Did you check both your power settings? I think there are settings in there to turn off your screen after a certain period of time. That might be it.

---

### Post by Dennis N on 2014-01-06
> **robbiek01 said:**
> Hi all, I'm running lubuntu 13.10, and my screen keeps going black after 10 minutes.


Lubuntu 13.10: Solution is to stop power manager from starting and blanking screen:

**Preferences > Default applications for LXSession**

In the dialog window,

Power Manager must be set to: **no**. Press Apply Button

(if you don't use apply, your choice won't be set)

Next time you start Lubuntu, Power Manager will not run.

---

