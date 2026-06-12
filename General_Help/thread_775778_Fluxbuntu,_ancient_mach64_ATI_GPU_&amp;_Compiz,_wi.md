---
title: "Fluxbuntu, ancient mach64 ATI GPU &amp; Compiz, will it blend?"
date: 2008-04-30
forum: General Help
---

### Post by UgniusS on 2008-04-30
**Edit:** Hi, according to some articles compiz fusion just will not work on mach64 card, it's way tooo old, so my experiment somehow finished without proper start.

My other question would be is there anything available like in 3D effects (or just using OpenGL to hardware accelerate window rendering) for fluxbox and mach64 card (or some window manager with 3d effects instead of fluxbox which would work on mach64).


**Old post:**
Hi,

may be I'm a bit crazy but I'm trying to launch compiz on old laptop with ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64) GPU running Fluxbuntu. May be it's not worth trying (will lag greatly if it will even start), but it's just an experiment. I am new to linux so usually I google about every bump on the ride. But it would be great if someone could help me with some guidance during my experiment. 

So far I have managed to enable direct rendering on my card, but now I am stuck at the very first step, installing Xgl, simply did apt-get install xserver-xgl, and rebooted. Now I cannot login, get an error that my session failed to start and this in my ~/.xsession-errors file:


> (process:5510): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5514): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
No matching visual for __GLcontextMode with visual class = 4 (32770), nplanes = 24
No matching visual for __GLcontextMode with visual class = 4 (32770), nplanes = 24
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.
No matching visual for __GLcontextMode with visual class = 4 (32770), nplanes = 24
No matching visual for __GLcontextMode with visual class = 4 (32770), nplanes = 24
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
manager.c:1387 (do_startup_configure) Directory /etc/ivman/ will be used for configuration files.
BScreen::BScreen: managing screen 0 using visual 0x2c, depth 16
apps file failure
X connection to :1.0 broken (explicit kill or server shutdown).

Segmentation fault

Any Ideas how to fix this?

Temporarily I have just disabled Xgl. By the way with fglrx driver instead of ati in xorg.conf, my X fails to start at all.

I can post any other log files or command results if needed.

Thank you very much for reading this, and I am sorry my engrish...

---

### Post by mcurran on 2009-10-29
I had desktop cube effect and others working with compiz and a Mach64 card back when I was running Linux Mint 4 "Daryna".  I have a ATI 3D RAGE LT PRO AGP 4MB GPU, and I used fglrx driver to accomplish that.  Now, however, I cannot get compiz working yet, I'll let you know if I have similar success with this kernel 2.6.31-14-generic (Karmic Koala).

---

