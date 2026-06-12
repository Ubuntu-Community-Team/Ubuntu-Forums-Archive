---
title: "Xserver wont start"
date: 2007-05-01
forum: General Help
---

### Post by jajabiner on 2007-05-01
Whenever i try to login through my user account xserver doesn't start. The login screen resolution is the highest(dont know exactly) and the resolution of my account  is 1024x768.
But when i start kububtu  in recovery mode xserver starts starts

when i console login through my user account and try startx i get this.

> 
X Window System Version 6.9.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 6.9
Build Operating System: FreeBSD 5.4 i386 [ELF]
Current Operating System: FreeBSD h4x0r.Dr_Death 5.4-RELEASE FreeBSD 5.4-RELEASE #0: Sun May 8 10:21:06 UTC 2005 [email]root@harlow.cse.buffalo.edu[/email]:/usr/obj/usr/src/sys/GENERIC i386
Build Date: 03 February 2007
Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 16 17:25:58 2007
(==) Using config file: "/etc/X11/xorg.conf"
_FontTransOpen: Unable to Parse address X11BASE/lib/X11/fonts/PORTNAME/AAHS
Could not init font path element X11BASE/lib/X11/fonts/PORTNAME/AAHS, removing from list!
_FontTransOpen: Unable to Parse address X11BASE/lib/X11/fonts/PORTNAME/AGA
Could not init font path element X11BASE/lib/X11/fonts/PORTNAME/AGA, removing from list!
_FontTransOpen: Unable to Parse address X11BASE/lib/X11/fonts/PORTNAME/FS
Could not init font path element X11BASE/lib/X11/fonts/PORTNAME/FS, removing from list!
_FontTransOpen: Unable to Parse address X11BASE/lib/X11/fonts/PORTNAME/Kasr
Could not init font path element X11BASE/lib/X11/fonts/PORTNAME/Kasr, removing from list!
_FontTransOpen: Unable to Parse address X11BASE/lib/X11/fonts/PORTNAME/MCS
Could not init font path element X11BASE/lib/X11/fonts/PORTNAME/MCS, removing from list!
_FontTransOpen: Unable to Parse address X11BASE/lib/X11/fonts/PORTNAME/Shmookh
Could not init font path element X11BASE/lib/X11/fonts/PORTNAME/Shmookh, removing from list!

(gnome-session:15039): GLib-GObject-WARNING **: IA__g_object_get_valist: object class `GnomeProgram' has no property named `goption-context'

Bonobo-ERROR **: file bonobo-ui-init-gtk.c: line 87 (add_gtk_arg_callback): assertion failed: (init_info != NULL)
aborting...

(process:15043): Gnome-CRITICAL (recursed) **: gnome_program_get_app_version: assertion `program->_priv->state >= APP_PREINIT_DONE' failed
aborting...
Multiple segmentation faults occurred; can't display error dialog

waiting for X server to shut down FreeFontPath: FPE "/usr/X11R6/lib/X11/fonts/misc/" refcount is 2, should be 1; fixing. 



Plsease help i just migrated from windows and i was hiving a great time with kubuntu till this happened.

---

### Post by bscbrit on 2007-05-01
Are you sure that you are running Ubuntu? Because your X11 system seems to be suggesting that it is FreeBSD!

[code]Build Operating System: FreeBSD 5.4 i386 [ELF]
Current Operating System: FreeBSD h4x0r.Dr_Death 5.4-RELEASE FreeBSD 5.4-RELEASE #0: Sun May 8 10:21:06 UTC 2005 root@harlow.cse.buffalo.edu:/usr/obj/usr/src/sys/GENERIC i386 [\code]

Have you done a fresh install from an ubuntu CD?

Of course, I may just be confused with the information that you have provided....

---

### Post by jajabiner on 2007-05-01
Sorry about that i get a similar error in the end. Didnt know how to save the error message.
Im running Kubuntu for sure

---

### Post by jajabiner on 2007-05-01
this message is from another website

---

### Post by jajabiner on 2007-05-01
that erro message was from another website

---

### Post by bscbrit on 2007-05-12
Jajabiner, did you get your screen working again?

---

### Post by GrueTamer on 2007-05-12
> **jajabiner said:**
> that erro message was from another websiteWe can't really help you without the exact error, but look in /var/log/Xorg.0.log for the crash log.

Note: you might want to do this from the livecd

---

