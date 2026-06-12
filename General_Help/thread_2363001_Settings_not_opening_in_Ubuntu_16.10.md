---
title: "Settings not opening in Ubuntu 16.10"
date: 2017-06-05
forum: General Help
---

### Post by ganesh3 on 2017-06-05
I am using GNOME shell on Ubuntu 16.10 with gnome version GNOME Shell 3.20.4. Below is the error. Please help.

sudo gnome-control-center
(switchboard:5261): Gtk-WARNING **: Theme parsing error: gtk-contained.css:118:2: Expected semicolon

(switchboard:5261): Gtk-WARNING **: Theme parsing error: gtk-contained.css:195:22: 'none' is not a valid color name

(switchboard:5261): Gtk-WARNING **: Theme parsing error: gtk-contained.css:252:20: 'solid' is not a valid color name

(switchboard:5261): Gtk-WARNING **: Theme parsing error: gtk-contained.css:538:22: 'none' is not a valid color name

(switchboard:5261): Gtk-WARNING **: Theme parsing error: gtk-contained.css:1846:34: 'theme_bg_color' is not a valid color name

(switchboard:5261): Gtk-WARNING **: Theme parsing error: gtk-contained.css:2780:28: Junk at end of value for background-color

(switchboard:5261): Gtk-WARNING **: Theme parsing error: gtk-contained.css:2807:24: 'solid' is not a valid color name

(switchboard:5261): Gtk-WARNING **: Theme parsing error: gtk-contained.css:4126:2: Expected semicolon

(switchboard:5261): Gtk-WARNING **: Theme parsing error: gtk-contained.css:4326:2: Expected semicolon

(switchboard:5261): Gtk-WARNING **: Theme parsing error: gtk-contained.css:4392:2: Expected semicolon

(switchboard:5261): Gtk-WARNING **: Theme parsing error: gtk-contained.css:4808:2: Expected semicolon

(switchboard:5261): Gtk-WARNING **: Theme parsing error: gtk-contained.css:4869:22: Not using units is deprecated. Assuming 'px'.
[INFO 10:52:42.169440] Application.vala:153: System Settings version: 2.0
[INFO 10:52:42.169483] Application.vala:155: Kernel version: 4.8.0-53-generic

** (process:5297): CRITICAL **: string_contains: assertion 'self != NULL' failed

** (process:5297): CRITICAL **: string_contains: assertion 'self != NULL' failed
[ERROR 10:52:45.389788] [GLib-GIO] Settings schema 'org.pantheon.desktop.gala.animations' is not installed
/usr/bin/gnome-control-center: line 20:  5261 Trace/breakpoint trap   (core dumped) switchboard $switchboard_options $requested_plug

---

### Post by LastDino on 2017-06-05
```
Settings schema 'org.pantheon.desktop.gala.animations' is not installed
```

This seems to be gnome shell package missing problem. Tried installing gnome-shell package? 

Please note: What suggested here if doesn't work you will be risking unable to boot, so please take full backup. There might be easier ways to deal with this, but this is what I think of.

---

### Post by ganesh3 on 2017-06-06
Thanks but will wait for other responses before I try yours.


Regards
Ganesh Bhat

---

