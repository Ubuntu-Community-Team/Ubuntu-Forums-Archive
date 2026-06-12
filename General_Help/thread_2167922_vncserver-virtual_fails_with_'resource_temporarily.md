---
title: "vncserver-virtual fails with 'resource temporarily unavailable' error"
date: 2013-08-15
forum: General Help
---

### Post by Sierra_Brown on 2013-08-15
I'm uncertain which section to post this in, so I apologize in advance if this was the wrong place.

I'm running Lubuntu 12.04 32 bit on my laptop, doing some experimenting with various systems I plan to put in place on a server I run in the future. Currently, I'm trying to get RealVNC server setup to run in virtual mode on my machine. However, I'm having an issue with it.

When I run 'vncserver-virtual' from terminal (As a user, not as root), the commandline outputs the following:

```
VNC(R) Server 5.0.5 (r106461) 
Built on Mar  4 2013 13:46:20
Copyright (C) 2002-2013 RealVNC Ltd.
VNC is a registered trademark of RealVNC Ltd. in the U.S. and in other
countries.
Protected by UK patent 2481870.
See http://www.realvnc.com for information on VNC.
For third party acknowledgements see:
http://www.realvnc.com/products/vnc/documentation/5.0/acknowledgements.txt
```

(There's a second or two then the rest of this pops up: )

```
Running applications in /etc/vnc/xstartup

VNC Server signature: 9a-92-8f-d6-58-f6-b7-be
Log file is /home/sierra/.vnc/sierra-laptop:1.log
New desktop is sierra-laptop:1 (192.168.1.121:1)
```

And then it seems to exit the process. I checked the log file mentioned in the output, and it displays this:

```
Underlying X server release 609000, The X.Org Foundation

VNC(R) Server (Virtual Mode) 5.0.5 (r106461)
Built on Mar  4 2013 13:49:26
Copyright (C) 2002-2013 RealVNC Ltd.
VNC is a registered trademark of RealVNC Ltd. in the U.S. and in other
countries.
Protected by UK patent 2481870.
See http://www.realvnc.com for information on VNC.
For third party acknowledgements see:
http://www.realvnc.com/products/vnc/documentation/5.0/acknowledgements.txt
<11> 2013-08-15T20:28:32.434Z sierra-laptop Xvnc[1895]: Zeroconf_t: Avahi domain not YET ready for services registration. Trying later
error opening security policy file /usr/X11R6/lib/X11/xserver/SecurityPolicy
Could not init font path element built-ins, removing from list!
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"
      after 779 requests (779 known processed) with 0 events remaining.
VNC Server - Virtual Mode: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
<11> 2013-08-15T20:28:33.098Z sierra-laptop Xvnc[1895]: AddClient: write: Broken pipe (32)
<11> 2013-08-15T20:28:33.099Z sierra-laptop Xvnc[1895]: Feature: Zeroconf: write: Broken pipe (32)
```

This right here seems to be the main issue:

```
VNC Server - Virtual Mode: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
```

I've tried specifying a different 'monitor' in the command via 'vncserver-virtual :2'. It still gives that error, but with :2 instead of :1.

The VNC server works perfectly fine if I run it in 'user mode' with the command 'vncserver-x11', and I can connect just fine with that. However, for the server, I need to features that the virtual desktop environment would provide.

---

