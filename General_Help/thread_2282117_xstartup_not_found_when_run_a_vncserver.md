---
title: "xstartup not found when run a vncserver"
date: 2015-06-12
forum: General Help
---

### Post by gary61 on 2015-06-12
sorry i'm a novice, lately i install the vncserver and intend to use vncserver for the remote GUI, i install xorg gdm and ubuntu-desktop, and the content of the root/.vnc/xstartup is like this 
```
#!/bin/sh# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session & #set starting GNOME desktop
#startkde & #kde desktop
#twm & #Text interface
#/usr/bin/startxfce4
#exec /usr/bin/fluxbox
```
and i login vncserver but it's dark it used to have twm but no GUI but now it's nothing
and the log file is like this 
```
Xvnc Free Edition 4.1.1 - built Mar 19 2015 19:23:29Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc




Fri Jun 12 09:17:19 2015
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/, removing from list!
sh: 1: /root/.vnc/xstartup: not found


Fri Jun 12 12:40:20 2015
 Connections: accepted: 0.0.0.0::2166
 SConnection: Client needs protocol version 3.4
 SConnection: Client uses unofficial protocol version 3.4
 SConnection: Assuming compatibility with version 3.3
 SConnection: AuthFailureException: Authentication failure
 Connections: closed: 0.0.0.0::2166 (Authentication failure)


Fri Jun 12 12:40:29 2015
 Connections: blacklisted: 0.0.0.0


Fri Jun 12 12:40:54 2015
 Connections: blacklisted: 0.0.0.0



```
really need some help

---

