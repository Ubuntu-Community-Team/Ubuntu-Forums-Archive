---
title: "Firefox/GNOME mouse-click error (7.04, 7.10)"
date: 2008-02-05
forum: General Help
---

### Post by Prioris on 2008-02-05
Hello!  I've been having a fairly annoying error with Firefox under GNOME, and I'm hoping someone can help.

Every so often, and with no apparent respect to what other applications are running, my Firefox window will begin acting very strangely in response to clicking.  Instead of a left-click activating a link or highlighting text and a right-click bringing up the Firefox context menu, a left click anywhere on-screen moves the Firefox window (brings up the four-way arrow pointer under vanilla GNOME; same pointer and window jiggles under Compiz) and a right-click brings up the desktop context menu (move, minimize/maximize, resize, move to workspace, etc).  Clicking other programs on the task bar has no effect, nor do any of the task bar menus or buttons work.

The only way to get out of this error mode is to use Alt-F2 --> xkill and kill the GNOME task bar. (Note that killing Firefox itself doesn't fix the problem!)  Once that's done, the task bar restarts itself and everything works fine for some non-trivial interval (10-15 min), but then it'll do the same thing again.  Likewise, Ctrl-Alt-Bksp'ing out of my session only resolves the problem for the same limited interval.  The only way to permanently stop the cycle is to shut down and restart, but then it's just a matter of time before it starts acting up again.  Initially I thought that the problem lay with GNOME alone, but since it never happens unless Firefox is running and on top of the screen, I have to suspect that the two are somehow destabilizing each other.

This problem has been occurring more or less continuously under both 7.04 and 7.10, and with all versions of Firefox from 2.0.0.4 to 3.0 b2.  I'm running a Toshiba Satellite M55, with a Pentium M 1.73 GHz processor, 1.5 GB of RAM and a 80 GB HDD (44 GB remaining).  Frankly, I'm at a loss as to what's causing this error or how to fix it.  Any ideas?

Thanks in advance!

---

