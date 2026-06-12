---
title: "Gimp: Configuring input devices dialog hangs after user input"
date: 2007-09-08
forum: General Help
---

### Post by optimarcus_prime on 2007-09-08
I just purchased a new Wacom Intuos3 6X8 Pen Tablet and installed it according to the instructions listed here: [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom).  The tablet installed correctly, and everything seems to be working properly, except for when I try to configure the tablet in a graphic program such as Gimp or Inkscape.

When I go to Preferences and then Input Devices, and finally Configure Extended Input Devices, the window hangs when I attempt to change the Device drop-down.  I've included screenshots.  The "Before" picture shows what it looks like before i hit the dropdown menu, and the "After" is after one of the dropdown options is chosen.

This issue has been reported before [[https://bugs.launchpad.net/gimp/+bug/76611](https://bugs.launchpad.net/gimp/+bug/76611)], but no solution was found.

When Gimp is run from the command line, this is the output when this error occurs:
```
/home/marcus/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'

(gimp:5111): Gtk-CRITICAL **: gtk_scrolled_window_add: assertion `bin->child == NULL' failed

(gimp:5111): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(gimp:5111): Gdk-CRITICAL **: gdk_drawable_get_colormap: assertion `GDK_IS_DRAWABLE (drawable)' failed

(gimp:5111): Gdk-CRITICAL **: gdk_window_set_background: assertion `GDK_IS_WINDOW (window)' failed

(gimp:5111): Gtk-CRITICAL **: gtk_scrolled_window_add: assertion `bin->child == NULL' failed

(gimp:5111): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(gimp:5111): Gdk-CRITICAL **: gdk_drawable_get_colormap: assertion `GDK_IS_DRAWABLE (drawable)' failed

(gimp:5111): Gdk-CRITICAL **: gdk_window_set_background: assertion `GDK_IS_WINDOW (window)' failed

```

Any thoughts?

---

### Post by optimarcus_prime on 2007-09-21
Bump.

---

