---
title: "[Unsolved] XFCE boot problem"
date: 2008-02-05
forum: General Help
---

### Post by cdaringe on 2008-02-05
Hey guys,
my xfce wont boot up. i posted the output in the .xsessions-errors file, but i cant make much sense of it. any tips?


(process:8233): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

[http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:8237): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

[http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 20: [[: not found
No default user directories
SESSION_MANAGER=local/cdcraptop:/tmp/.ICE-unix/8230
Initializing gnome-mount extension
Window manager warning: Failed to read saved session file /home/cdaringe/.metacity/sessions/default0.ms: Failed to open file '/home/cdaringe/.metacity/sessions/default0.ms': No such file or directory
** Message: Not starting remote desktop server
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1800022 (awn_elemen)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
PID TTY TIME CMD

---

