---
title: "Failed to start X Server - LiveCD"
date: 2007-03-03
forum: General Help
---

### Post by BuntuConversion on 2007-03-03
I burned a LiveCD and rebooted; the Ubuntu screen came up, I chose install or start Ubuntu.  It did its little scrolling bar, then gave me the following error:

Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?

I chose yes.  Saw this:

Window System version 7.1.1
Release Date: 12 May 2006
Protocol version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 1686
Current Operating System: Linux ubuntu 2.6.17-10-generic #2
Oct 13 18:45:35 UTC 2006 1686
Build Date: 07 July 2006
     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
     to make sure that you have the latest version
Module loader present
Markers: (--) probed, (**) from config file, (==) default set
              (++) from command line, (!!) notice, (II) information
              (WW) warning, (EE) error, (NI) not implemented, (??) *don't remember this*
(==) Log file: "/var/log/xorg.0.log", Time: Fri Mar 2 20:05
(==) using config file: "/etc/X11/xorg.conf"

then it had

-> Input Device "cursor"
-> Input Device "eraser"
The directory "/usr/share/x11/fonts/misc" does not exist.
     Entry deleted from font path
The directory "/usr/share/x11/fonts/cyrillic" does not exist.
     Entry deleted from font path
The directory "/usr/share/x11/fonts/100dpi" does not exist.
     Entry deleted from font path
The directory "/usr/share/x11/fonts/75dpi" does not exist.
     Entry deleted from font path

and on and on, then it had

The X server is now disabled.  Restart GDM when it is configured correctly.    <OK>

THEN it took me to a blank screen with a flashing cursor.  I could type and hit enter, but nothing happened.  I hit the power button once and it beeped, held it and it reset.

What did I do wrong?  How can I fix it?

I am trying to run it on a Dell Dimension E510.

---

### Post by zvacet on 2007-03-03
```
sudo dpkg-reconfigure xserver-xorg
```

---

