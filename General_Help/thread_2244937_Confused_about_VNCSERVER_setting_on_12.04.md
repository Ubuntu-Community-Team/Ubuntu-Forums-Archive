---
title: "Confused about VNCSERVER setting on 12.04"
date: 2014-09-19
forum: General Help
---

### Post by G_Wong on 2014-09-19
Hi,

I upgraded our server to 12.04.5 LTS recently, trying to run vncserver on it but not much luck so far, I actually have 3 questions:

1. There are "vncserver", vnc4server" and "tightvncserver", which one should I be using? Is there a link to explain the differences among them? 

2. I ran vncserver, then I try to vnc from a laptop, I got the connection, session opened fine, desktop icons show up but there is no top menu title bar, I can browse the net, watch youtube video but cannot resize or min/max any window. I browsed the forum, must have tried 30 different xstartup suggested versions, most got worse, none got me the title bar. Here are the xstartup and log file :

[U]xstartup

[/U]#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP #Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
exec /usr/bin/gnome-session --session=gnome-classic &

[U]Log file

[/U]18/09/14 18:07:45 Xvnc version TightVNC-1.3.9
18/09/14 18:07:45 Copyright (C) 2000-2007 TightVNC Group
18/09/14 18:07:45 Copyright (C) 1999 AT&T Laboratories Cambridge
18/09/14 18:07:45 All Rights Reserved.
18/09/14 18:07:45 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
18/09/14 18:07:45 Desktop name 'X' (laptop:99)
18/09/14 18:07:45 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
18/09/14 18:07:45 Listening for VNC connections on TCP port 5999
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
xrdb: No such file or directory
xrdb: can't open file '/home/abcxyz/.Xresources'
18/09/14 18:08:10 Got connection from client 192.168.1.123
18/09/14 18:08:10 Using protocol version 3.8
18/09/14 18:08:13 Full-control authentication passed by 192.168.1.123
18/09/14 18:08:13 Pixel format for client 192.168.1.123:
18/09/14 18:08:13   32 bpp, depth 24, little endian
18/09/14 18:08:13   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
18/09/14 18:08:13   no translation needed
18/09/14 18:08:13 Enabling full-color cursor updates for client 192.168.1.123
18/09/14 18:08:13 rfbProcessClientNormalMessage: ignoring unknown encoding -223
18/09/14 18:08:13 rfbProcessClientNormalMessage: ignoring unknown encoding 16
18/09/14 18:08:13 Using hextile encoding for client 192.168.1.123
18/09/14 18:08:13 Enabling full-color cursor updates for client 192.168.1.123
18/09/14 18:08:13 rfbProcessClientNormalMessage: ignoring unknown encoding -223
18/09/14 18:08:13 Using hextile encoding for client 192.168.1.123
18/09/14 18:08:13 rfbProcessClientNormalMessage: ignoring unknown encoding 16
18/09/14 18:12:54 rfbProcessClientNormalMessage: read: Connection reset by peer
18/09/14 18:12:54 Client 192.168.1.123 gone
18/09/14 18:12:54 Statistics:
18/09/14 18:12:54   key events received 88, pointer events 1792
18/09/14 18:12:54   framebuffer updates 4071, rectangles 5750, bytes 1942003056
18/09/14 18:12:54     cursor shape updates 131, bytes 100292
18/09/14 18:12:54     copyRect rectangles 167, bytes 2672
18/09/14 18:12:54     hextile rectangles 5452, bytes 1941900092
18/09/14 18:12:54   raw bytes equivalent -1118523900, compression ratio -0.575995
Terminated
** (gnome-session:5707): WARNING **: Cannot open display: 


3. On the same server, I got the above described issue every time with my login but when we logged in with a different user account, using the same xstartup file, we only got a blue screen and a cursor from the client, no icons.

I am really confused, the server used to run mandriva linux and we were able run vncserver from different accounts and vnc into it no problem for the last year or so, not sure what we are doing wrong in Ubuntu, help will be much appreciated.

Thanks

---

### Post by G_Wong on 2014-09-21
Just wondering, any suggestion or pointer to links to resolve this?

Thanks

---

