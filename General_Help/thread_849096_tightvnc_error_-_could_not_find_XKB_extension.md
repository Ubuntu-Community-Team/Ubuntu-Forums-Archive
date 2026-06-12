---
title: "tightvnc error - could not find XKB extension"
date: 2008-07-04
forum: General Help
---

### Post by lukemack on 2008-07-04
Hi,

I have installed tightvncserver and am getting the following errors when starting the process (from the log file)

```

04/07/08 08:58:26 Xvnc version 3.3.tight1.2.9
04/07/08 08:58:26 Copyright (C) 1999 AT&T Laboratories Cambridge.
04/07/08 08:58:26 Copyright (C) 2000-2002 Constantin Kaplinsky.
04/07/08 08:58:26 All Rights Reserved.
04/07/08 08:58:26 See http://www.uk.research.att.com/vnc for information on VNC
04/07/08 08:58:26 See http://www.tightvnc.com for TightVNC-specific information
04/07/08 08:58:26 Desktop name 'X' (deepthought:1)
04/07/08 08:58:26 Protocol version supported 3.3
04/07/08 08:58:26 Listening for VNC connections on TCP port 5901
Font directory '/usr/X11R6/lib/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/100dpi/' not found - ignoring
xrdb: No such file or directory
xrdb: can't open file '/home/luke/.Xresources'
Option '--login' is no longer supported in this version of gnome-terminal; you m
ight want to create a profile with the desired setting, and use the new '--windo
w-with-profile' option
Window manager warning: Log level 32: could not find XKB extension.


```

I am unable to connect from a remote machine (I have enabled the relevant ports in the firewall) so am assuming these log errors are the cause.

many thanks

lukemack.

---

