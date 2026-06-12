---
title: "[SOLVED] Compiz fails to start, X not happy"
date: 2007-11-24
forum: General Help
---

### Post by jken146 on 2007-11-24
I get the following error message when I log into Gnome.  It appears compiz is not starting.

From ~/.xsession-errors :
```

(process:9274): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:9278): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/jon-desktop:/tmp/.ICE-unix/9271
** Message: Not starting remote desktop server
Checking for Xgl: Initializing gnome-mount extension
** Message: failed to load session from /home/jon/.nautilus/saved-session-V0HE2T
not present. 

** (nautilus:9334): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:9334): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:9334): WARNING **: Can not get _NET_WORKAREA

** (nautilus:9334): WARNING **: Can not determine workarea, guessing at layout


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 10
Detected PCI ID for VGA: 01:00.0 0300: 10de:0221 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: 
(tilda:9376): Gdk-CRITICAL **: gdk_window_set_geometry_hints: assertion `GDK_IS_WINDOW (window)' failed

(tilda:9376): Gdk-CRITICAL **: gdk_window_move: assertion `GDK_IS_WINDOW (window)' failed
present. 
Checking for non power of two support: Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

(gnome-desktop-item-edit:9353): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
gnome-desktop-item-edit: no file to edit

(evolution-alarm-notify:9373): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
evolution-alarm-notify-Message: Setting timeout for 66368 1195948800 1195882432
evolution-alarm-notify-Message:  Sun Nov 25 00:00:00 2007

evolution-alarm-notify-Message:  Sat Nov 24 05:33:52 2007


(gnome-power-manager:9357): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:9362): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:9364): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

```

It seems to have saved an open terminal window from my last working session, so luckily I am able to enter ```
compiz --replace
``` and restore nearly full functionality.  I tried to get compiz starting at startup by going to the Sessions applet in Preferences, but this failed to appear, then by creating a startup script in /usr/local/bin - this didn't do the trick either.

I'd appreciate any help.

---

### Post by jken146 on 2007-11-28
bump

---

### Post by jken146 on 2007-11-29
I'm marking this as solved because I deleted all my configuration files and reinstalled Ubuntu.  I've got compiz working fine now.

---

