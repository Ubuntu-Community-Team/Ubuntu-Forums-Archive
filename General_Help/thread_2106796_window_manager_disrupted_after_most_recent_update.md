---
title: "window manager disrupted after most recent update"
date: 2013-01-20
forum: General Help
---

### Post by DrScum on 2013-01-20
With a 12.04 LTS system set to Gnome fallback I installed the most recent updates from the update manager. After restarting the window management is all messed up:

compositing no longer working, the mouse pointer disappears and reappears at random.

How do I diagnose and fix this kind of problem?

---

### Post by DrScum on 2013-01-20
In the meantime I've done some testing on window management. It looks like the problem is compis. The following messages I get when I try to restart compis with the followin command:

compiz --replace

Warn: requested a pixmap type decoration when compositing isn't available
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: Root visual is not a GL visual
Xlib:  extension "GLX" missing on display ":0.0"

Can anyone help me to get a grip on this?

---

### Post by DrScum on 2013-01-20
I found the problem:

during the update the nvidia display driver apparently got disabled. I had to go to System Settings>Additional Drivers and install the current nvidia driver. After that things were back to normal.

This is something that shouldn't happen I think!

---

