---
title: "Ubuntu pulled a Window$ on me!-Computer froze than showed gibberish! (xsession.error)"
date: 2006-12-18
forum: General Help
---

### Post by emarkay on 2006-12-18
While on the forums here, suddenly everything froze.  then a few seconds later I got 2 screens of random video noise, than nothing - resetting the PC caused a shutdown.  I rebooted and, well here I am.

I THINK this is the error log....
************

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "xxxxxx"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/xxxxxx-desktop:/tmp/.ICE-unix/4797
Password:

(gnome-panel:5114): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 26

Gdk-WARNING **: Missing charsets in FontSet creation


Gdk-WARNING **:     JISX0208.1983-0


Gdk-WARNING **:     KSC5601.1987-0


Gdk-WARNING **:     GB2312.1980-0


Gdk-WARNING **:     JISX0201.1976-0

send: Bad file descriptor
connect: Connection refused
connect: Operation now in progress
Window manager warning: Log level 16: Error loading GPOS table 4097

** (nautilus:5112): WARNING **: No description found for mime type "x-special/socket" (file is "mapping-xxxxxx"), please tell the gnome-vfs mailing list.

************
Um, what's it mean, what do I do, and how do I prevent my PC from locking up again?

---

### Post by pay on 2006-12-18
I think that it is a problem with your video card. Make sure that the video card has it's drivers installed correctly.

---

### Post by emarkay on 2007-02-01
Was just a one time glitch - must have been lightning on Jupiter or something...

---

