---
title: "XGL session problem, logged out after 5 seconds"
date: 2007-01-18
forum: General Help
---

### Post by skelter15 on 2007-01-18
I am a newbie in Ubuntu and in XGL. 
Half a year ago I installed a dual-boot system (windows and ubuntu). First ubuntu, then windows. After that I made XGL working, and using both the default session as well as the XGL session. But since a couple of weeks, when I trie to enter the XGL session, the systems logs me out with the following message (the ~/.xsession-errors file):

[FONT="Georgia"]/etc/gdm/PreSession/Default: registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp/ -x "/var/lib/gdm/:0. Xservers" -h "" -l ":0" "Jelte"
/etc/gdm/Xsession: Beginning session setup...
Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
SESSION_MANAGER=local/Jelte:/tmp/.ICE-unix/5009
Gnome-Message: gnome_execute_async_with_env_fds: returing -1
XXXXXXXXXXXXXXXXXXXXX WARN ONCE XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
File radeon_mm.c function radeon_mm_alloc line 216
Ran out of GART memory!
Please consider adjusting GARTSize option.
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
(gnome-panel: 5078): GdkPixbuf -Critical **: gdk_pixbuf_scale_simple: assertion `dest_wdth > 0' failed
Try R300_SPAN_DISABLE_LOCKING env var if this hangs.

(gnome-panel: 5078): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allovate widget with width -11 and height 24
Error: Could nog get dma buffer... exiting.

The application 'update notifier' lost its connection to the display :1.0;
most likely the X server was shut down or you killed/destroyed the application

The application 'gnome-session' lost its connection to the display :1.0;
most likely the X server was shut down or you killed/destroyed the application

The application 'nautilus' lost its connection to the display :1.0;
most likely the X server was shut down or you killed/destroyed the application

The application 'gnome-cups-icon' lost its connection to the display :1.0;
most likely the X server was shut down or you killed/destroyed the application
[/FONT]

I am using an ATI Radeon 9600 video card.
Does someone recognizes this error? And knows the solution?
I searched a lot, but did not found the same problem. I am not very familiar with the terminal and the command lines, so please take it slowly :D 

Thanks in advance...

---

### Post by skelter15 on 2007-01-19
Anyone with the same problem? Or a-look-alike? 
Try, please...

---

