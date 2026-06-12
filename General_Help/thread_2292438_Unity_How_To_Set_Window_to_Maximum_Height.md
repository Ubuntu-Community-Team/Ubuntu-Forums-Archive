---
title: "Unity How To Set Window to Maximum Height"
date: 2015-08-28
forum: General Help
---

### Post by 7-webmaster on 2015-08-28
Most window managers display windows in one of three sizes: normal, full-screen, and minimized (e.g. on the task bar).

Unity has FOUR sizes.  It adds a "snapped to max height/width" size.  But even though Unity temporarily displays the window in that size it does not remember that the I requested that the window be maximum height or width.  This creates extra steps.  There is no way to get from full-screen back to "snapped" size except by going to "normal" size and then dragging the window to "snapped" size, again.  And then repeat that the next cycle.  And then repeat that the next cycle. ad infinitum.

I want to make the "normal" size of a window the maximum height, but Unity will not let me.  It keeps "restoring" the window to what Unity insists is the "normal" size of the window, which is NOT the size that I set it to.  This is frustrating.  If I make a window maximum height then I damn well want that window to be maximum height, and not some other size that Unity "thinks" is what I want.

So how do I convince Unity that the "normal" size of a window is the maximum height, and not the size that I intentionally dragged the window from.

---

### Post by kerry_s on 2015-08-28
i don't see those kind of settings in compizconfig.

i think it's the app that does the size/position remembering & only if it's written to do that.

---

### Post by vasa1 on 2015-08-28
Maybe OP can try some *wmctrl* magic? Make the EXE= line of the .desktop file for an application use a script that maximizes the height?

---

