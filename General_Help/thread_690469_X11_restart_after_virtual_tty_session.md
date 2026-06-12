---
title: "X11 restart after virtual tty session"
date: 2008-02-07
forum: General Help
---

### Post by jimzat on 2008-02-07
I am running Feisty on a dell Optiplex 170L with a Radeon dual display card installed.

For the past several months I have been using the dual displays without a problem and recently added a third monitor connected to the integrated (Intel 82865G) video card.  After some work I am now able to run all three monitors.

Under my previous configuration (2 monitors) whenever I would go to a virtual tty it would display (in parallel) on both monitors. But other than that all was OK.

Now when I bring up a virtual tty it is displayed on the monitor connected to the integrated adapter (which is fine).  Under this new configuration when I try to go back to my X session (Ctrl-Alt-F7), the X server seems to reboot and brings me back to the gdm login screen (losing all of my "work in progress".

I took a look at the Xorg.0.log files and nothing umps out at me.  Any ideas?

jimzat

---

### Post by jimzat on 2008-02-12
Does anybody have any suggestions what to look for or where to look?

jimzat

---

