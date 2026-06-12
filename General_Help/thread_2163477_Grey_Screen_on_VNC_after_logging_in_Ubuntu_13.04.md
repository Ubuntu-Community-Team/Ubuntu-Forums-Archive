---
title: "Grey Screen on VNC after logging in Ubuntu 13.04"
date: 2013-07-18
forum: General Help
---

### Post by Bourn on 2013-07-18
I've read, searched,referred and applied numerous solutions from the Internet, NOTHING WORKS. 

That damned grey screen simply wont go.

Here's /.vnc/xstartup

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#xfce4-session &
startxfce4 &


and here's VNC server log,

18/07/13 10:59:21 Xvnc version TightVNC-1.3.9
18/07/13 10:59:21 Copyright (C) 2000-2007 TightVNC Group
18/07/13 10:59:21 Copyright (C) 1999 AT&T Laboratories Cambridge
18/07/13 10:59:21 All Rights Reserved.
18/07/13 10:59:21 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
18/07/13 10:59:21 Desktop name 'X' (Sammy:1)
18/07/13 10:59:21 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
18/07/13 10:59:21 Listening for VNC connections on TCP port 5901
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
sh: 1: /root/.vnc/xstartup: Permission denied


18/07/13 10:59:46 Got connection from client 123.237.171.127
18/07/13 10:59:47 Non-standard protocol version 3.4, using 3.3 instead
18/07/13 10:59:51 Full-control authentication passed by 123.237.171.127
18/07/13 10:59:52 Pixel format for client 123.237.171.127:
18/07/13 10:59:52   16 bpp, depth 16, little endian
18/07/13 10:59:52   true colour: max r 31 g 63 b 31, shift r 11 g 5 b 0
18/07/13 10:59:52   no translation needed
18/07/13 10:59:52 Using hextile encoding for client 123.237.171.127
18/07/13 10:59:52 rfbProcessClientNormalMessage: ignoring unknown encoding 16
18/07/13 10:59:52 rfbProcessClientNormalMessage: ignoring unknown encoding 9
18/07/13 10:59:52 rfbProcessClientNormalMessage: ignoring unknown encoding 8
18/07/13 10:59:52 Using compression level 6 for client 123.237.171.127
18/07/13 10:59:52 Enabling X-style cursor updates for client 123.237.171.127
18/07/13 10:59:52 Enabling cursor position updates for client 123.237.171.127
18/07/13 10:59:52 Using image quality level 6 for client 123.237.171.127
18/07/13 10:59:52 rfbProcessClientNormalMessage: ignoring unknown encoding -65530
18/07/13 10:59:52 Enabling LastRect protocol extension for client 123.237.171.127
18/07/13 10:59:52 rfbProcessClientNormalMessage: ignoring unknown encoding -223
18/07/13 11:00:02 Client 123.237.171.127 gone
18/07/13 11:00:02 Statistics:
18/07/13 11:00:02   key events received 0, pointer events 156
18/07/13 11:00:02   framebuffer updates 1, rectangles 3, bytes 399470
18/07/13 11:00:02     cursor shape updates 1, bytes 82
18/07/13 11:00:02     cursor position updates 1, bytes 12
18/07/13 11:00:02     hextile rectangles 1, bytes 399376
18/07/13 11:00:02   raw bytes equivalent 1572876, compression ratio 3.938334

That's the snapshot of this annoying grey screen - [COLOR=#111111][FONT=Helvetica Neue]http://i.imgur.com/MlqXXfl.jpg[/FONT][/COLOR]

I'm tired, frustrated and cant think of anything anymore. So HELP !!

---

### Post by steeldriver on 2013-07-18
it looks like you are trying to start the vnc server as root - so it is looking for /root/.vnc/xstartup instead of *your* ~/.vnc/xstartup

also you probably don't want to exec /etc/vnc/xstartup (if it exists) because that would exit the current script before reaching your personal session commands

---

### Post by Bourn on 2013-07-18
Yes I'm doing as root. So ?

My xstartup file is located in /root/.vnc.

Do you have a solution please ?

---

### Post by steeldriver on 2013-07-18
is the root xstartup file executable?

imho it's never good to run an X session as root let alone a *remote*  X session

---

### Post by Bourn on 2013-07-18
It wasn't, I did now. Restarted VNC server, still the same situation.
I've always ran every application under root since years, never had a problem like this.

---

