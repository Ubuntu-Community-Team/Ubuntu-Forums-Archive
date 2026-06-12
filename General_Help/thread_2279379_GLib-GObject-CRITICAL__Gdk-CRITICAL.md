---
title: "GLib-GObject-CRITICAL ** Gdk-CRITICAL **"
date: 2015-05-23
forum: General Help
---

### Post by eival on 2015-05-23
omg this error is driving me insane, its been happening only recently, prior on 14.04 and still after upgrading to 15.04, i see similar bug reports going back YEARS

someone tell me how to fix this, its extremely annoying

(firefox:20503): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion 'GDK_IS_WINDOW (window)' failed
(firefox:20503): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

causes my entire UI outside of the mouse cursor (and audio since it ALWAYS happens when im playing some type of media either in firefox or VLC/chrome when it happens so the media will continue to play in the background and the mouse cursor will roam around just fine....and the most annoying issue, killing the UI with ctrl alt f1 through 4 does nothing

it will kill the monitor that has the launcher and then will take literally a minute or more before then my 2nd which is connected via VGA (which makes me think the launcher placement matters since the VGA signal would and is traditionally faster than the DVI that my main monitor has) it takes equally as long to then reenable the UI with CA F7 or which ever it is and then the same length to then fall back into tty

sometimes im lucky and rather than a complete freeze it will simply chug along and take forever to load the browser closure buttons on the full screen bar and i can close it that way.

would there be an additional log inside firefox that could tell me more?

---

