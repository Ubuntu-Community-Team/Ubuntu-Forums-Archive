---
title: "Sudden error.. I don't think I provoked this.."
date: 2007-09-15
forum: General Help
---

### Post by sandman85 on 2007-09-15
After logging into Ubuntu a few days ago (which I hadn't done for a long time before that) I got an unexpected error:> Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.Well, I logged into the failsafe session, and I have no idea what's wrong. I know I'm not out of diskspace.. but there's more. I looked at the xsession.errors file that it showed me:```
(process:5671): Gtk-WARNING **: This process is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead. For further details, see gtk.org/setuid.html.

Refusing to initialize GTK+.
/etc/gdm/xsession: Beginning session setup...
/etc/X11/xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found
Checking for nVidia: present.
Starting xgl with options: -accel xv:fbo -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama
xmodmap: unable to open display ':1'
Fatal server error: no GLX visuals available
(x-session-manager:5668): Gtk-WARNING **: cannot open display:
```I have to admit, I'm a pretty big newbie when it comes to Linux. Does anyone have the faintest idea what is going on here?

Thanks,
sandman85

---

