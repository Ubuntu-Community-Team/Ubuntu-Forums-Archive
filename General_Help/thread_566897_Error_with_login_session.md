---
title: "Error with login session"
date: 2007-10-04
forum: General Help
---

### Post by j o e l on 2007-10-04
I've tried researching the forums and found many similar issues, but none of the stated solutions matched my scenario...

When I login to Ubuntu, the splash screen  appears to load the Gnome desktop, but as it is seemingly loading, it goes right back to the login screen.  If I login with the same user account, it loads the desktop on the 2nd attempt.  However, an error message displays with the following message:

[INDENT]Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.[/INDENT]

A more detailed error message accompanying this states:

[INDENT]/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "joel"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/BaseCamp-Edgy:/tmp/.ICE-unix/6063
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

(gnome-cups-icon:6139): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6135): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(epiphany:6140): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
Session management error: IO error occured opening connection

(bluefish:6151): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
bluefish 1.0.7 HTML editor
Usage: bluefish [options] [filenames ...]

Currently accepted options are:
-s           skip root check
-v           current version
-n           open new window
-p filename  open project
-h           this help screen

(evince:6153): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gedit:6155): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(yelp:6172): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnucash:6154): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:6133): GnomeUI-WARNING **: While connecting to session manager:
IO error occured doing Protocol Setup on connection.

(gnome-terminal:6134): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.[/INDENT]

An interesting note is that I can login on the first attempt wiithout any issues when using my wife's user account.

Does anyone have any ideas to try?

I appreciate your help...

-- joel

---

### Post by j o e l on 2007-10-04
For anyone else who might need this...I deleted ./gnome2/session, and that did the trick.

---

