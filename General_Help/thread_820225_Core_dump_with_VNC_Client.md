---
title: "Core dump with VNC Client"
date: 2008-06-06
forum: General Help
---

### Post by nickrodin on 2008-06-06
Running Real VNC has been a cakewalk with other operating systems, but with
Ubuntu 7.10 is turning out to be a real pain.

After installing VNC 4.1 I tried to run the viewer, but it complained about a
missing libstdc++-libc6.2-2.so.3. I couldn't find this anywhere on the 
Ubuntu site (or any libraries, for that matter) so, assuming that Linux is
Linux wherever you go, I went to Debian and installed the  	 libstdc++2.10-glibc2.2 package.

I was then able to get vncviewer to open a dialog, but then when I try to 
connect to any server, it core dumps.  No error message, no nothing, just a
core dump.

I tried running vncserver and got this output in the log:

---------------------------------------------------------------------------

Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'

Xvnc Free Edition 4.1.2 - built May 12 2006 17:42:24
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 40201000, The XFree86 Project, Inc


Thu Jun  5 23:08:41 2008
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5902
 vncext:      created VNC server for screen 0
error opening security policy file /usr/X11R6/lib/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!

Fatal server error:
could not open default font 'fixed'
xsetroot:  unable to open display 'nick-desktop:2'
/home/nick/.vnc/xstartup: 7: twm: not found
vncconfig: unable to open display "nick-desktop:2"
xterm Xt error: Can't open display: nick-desktop:2

---

