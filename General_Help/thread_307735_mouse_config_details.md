---
title: "mouse config details"
date: 2006-11-27
forum: General Help
---

### Post by milhouse on 2006-11-27
I'm running edgy with a gvision touchscreen monitor.  Everything works great except for a few nagging details I'm trying to address.  

First, double clicks (or "taps" in this case) in Gnome.  The issue is not the timing between taps, but the spatial relationship between the taps.  It's too small right now and I need to open it up a bit.  I have found references in the gtk+ manual to "gtk-double-click-distance" but I can't figure out if this is set at compile time or it can be configured.  Anyone know?

My second issue is sort of related to the first.  The Gnome menus are difficult to use with a touchscreen.  Traversing the menus is simple, but *selecting* something is difficult.  If, for example, you simply tap System->Prefs->Screensaver the menus just disappear.  You can tap System->Prefs but then you have to press and just barely roll your fingertip to "click" on Screensaver.  But if you roll your finger too much it registers a click and drag and a shortcut to screensaver is placed on the desktop.  I would bet that if issue 1 is resolved, at least there would be more leeway on the "roll to click" which would make it a bit easier, but it would be nice to just be able to tap to select.  Again, hope may lie in the gtk settings but where would these be?  Are they application specific?  Or is there one gtk+ config file or are these options compiled in?


As an aside, this Gvision P15BX-AB-459G monitor ships with honest-to-goodness linux drivers that work great with Xorg and a calibration tool that runs unprivileged.  Setup is a snap.  Worth looking into if you're in the market for an inexpensive touchscreen.

---

