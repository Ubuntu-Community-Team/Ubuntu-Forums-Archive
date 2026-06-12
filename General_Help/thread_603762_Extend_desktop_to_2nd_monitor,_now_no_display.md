---
title: "Extend desktop to 2nd monitor, now no display"
date: 2007-11-05
forum: General Help
---

### Post by schroede on 2007-11-05
I installed the current distribution recently, and really like Ubuntu, but then tried extending my desktop to a second monitor (a TV) via the GUI.  It told me I needed to logout and back in, but then it provided no graphical display at all.  Rebooting, I get the tty output but it does not switch into graphical mode.

So, via the command line or editing files, how to I switch it back to single monitor mode?

I tried booting in recovery mode, and running 
dpkg-reconfigure xserver-xorg
which seemed to operate OK, but didn't fix the problem.

I checked recently updated files in /etc, but didn't see anything obvious.

The log indicates:
No core pointer
Fatal server error:
failed to initialize core devices

Hopefully, I didn't break anything else via mulitple reboots...
Thanks,
 - Wayne -

---

### Post by schroede on 2007-11-11
After searching and trying a few things, I now have it working.  Here are some of the answers to my questions:

What I had done was System->Administration->Screens and Graphics and then
clicking screens2 and extend to the right.

The file updated is /etc/X11/xorg.conf which is the configuration file for the X-Windows server.

Within that, it says that running dpkg-reconfigure will reset the file, and this ran OK on my PC but somehow didn't fix my problem.

What worked, was for me to edit xorg.conf (saving a copy first), removing some of the lines about the second screen (screen 1).  Then, rebooting in normal mode, it came up OK.

But then, there were two problems: the desktop was larger than the screen (so I had to move the mouse to the edge to see each side), and the change screen resolution was no longer working.

So solve this, I eventually booted from the CD, verified that this all worked fine from that, and then copied the xorg.conf file.  Then I booted in recovery mode to put it in place, and when I booted in normal mode it worked fine, the xserver coming up fine, and the above 2 problems also fixed.

As far as I can tell, extending the screen did not make a copy of the xorg.conf file, altho other types of updates do.  So it would be nice if it would do that.  But now I know to save a copy of it before using the GUI to try to extend to a second monitor.

 - Wayne Schroeder -

---

