---
title: "brightness not longer controlled by power management"
date: 2008-01-20
forum: General Help
---

### Post by yingjai on 2008-01-20
On fresh install, brightness was controllable through power management. I can slide the dimmer left and right and the screen will go dim or bright. After I installed some apps and updates, this no longer worked. When I unplug the power, power management senses it's on battery and tries to dim the screen but nothing happens. My laptop is a Vaio VGN-T250P and I can still control brightness manually though FN+F6/F7.

---

### Post by rosegarden78 on 2008-01-21
I heard the brightness slider is no longer present.  Try typing this command in a terminal

xgamma -gamma 0.75
xgamma -gamma 1.0

You can assign these commands as keyboard shortcuts if you write a shell script and use bash.

---

### Post by yingjai on 2008-01-21
No no. Sorry if my post was confusing. I don't need keyboard shortcuts to change screen brightness because FN key works.

My problem is that power management does not control screen brightness anymore meaning when laptop goes into battery mode, screen does not dim.

---

### Post by rosegarden78 on 2008-01-22
I've seen more than 30 threads on this topic every time I suggest trying gamma correction.  I have yet to find a way to control brightness or back-light with the GUI.  People say the old power manager had a slider but I've never used it.

---

