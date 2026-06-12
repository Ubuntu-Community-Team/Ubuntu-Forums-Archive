---
title: "XGL suddenly not letting me re-login"
date: 2007-11-02
forum: General Help
---

### Post by axsys on 2007-11-02
so first, here is how my problem started:

 i was messing around with trying to install a plugin for compiz today and couldnt get it to work, so i tried installing the git version of compiz and couldnt get that to work either, so i reinstalled the stable version of compiz using synaptic and everything seemed fine. after i restarted, i needed to restart X at one point so i did ctrl+alt+backspace like normal but when i logged in i immediately got a "your session lasted less than 10 seconds" box with an attached .xseission-errors file, clicked ok, then got kicked back to the login window.

well now i have to login to a failsafe gnome every time i have to restart X. however, if uninstall xserver-xgl, everything works just fine. so im not sure exactly whats going on, since i didnt touch anything with xgl today. anyone ever heard of this? here is .xsession-errors looks like when i do a first boot up:

```

(process:5644): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5648): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
xmodmap:  unable to open display ':1'
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SESSION_MANAGER=local/axsys-ubuntu:/tmp/.ICE-unix/5641
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
Initializing gnome-mount extension
** Message: Not starting remote desktop server
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Conky: desktop window (e000b2) is subwindow of root window (52)
Conky: window type - override
Conky: drawing to created window (2000001)
Conky: drawing to double buffer
```

and heres what it says when i try to log back in:

```


(process:6478): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:6482): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
xmodmap:  unable to open display ':2'

(x-session-manager:6475): Gtk-WARNING **: cannot open display:  
```

i would appreciate any advice to fix this. thanks in advance!

---

### Post by superyear on 2007-12-28
I found a solution on this URL: [https://bugs.launchpad.net/ubuntu/+bug/136529](https://bugs.launchpad.net/ubuntu/+bug/136529)

In summary, the solution is:

[FONT="Fixedsys"]sudo chmod a+w /tmp; sudo chmod o+t /tmp[/FONT]

Some update applied changed the permission on /tmp directory... :confused:

---

### Post by rmores on 2007-12-30
just had the same problem. restored my system from a tar backup and that happened. after restoring permission to the tmp folder everythings fine. thx!

---

