---
title: "VNC connection - gray screen"
date: 2018-01-23
forum: General Help
---

### Post by drieske2 on 2018-01-23
Hi,
I've installed the Ubuntu Desktop (16.04.3 LTS), which comes with the Unity Desktop Environment.

The desktop is convenient to configure some settings, but my Ubuntu is actually running headless. I installed "TeamViewer Host" so I'm able to log on to the environment now and then. What I noticed is that when my Intel NUC is connected to a display, my teamviewer connection is very responsive. After disconnecting the display, my Teamviewer is extremely slow. I've read somewhere that this is because the graphic card is not used to build your screen when a screen is connected.

So I wanted to try VNC as an alternative. 
I followed [this tutorial]("https://linode.com/docs/applications/remote-desktop/install-vnc-on-ubuntu-16-04/") to set up a VNC connection.
I'm using VNC Viewer from RealVNC on a Windows desktop to make the connection.
I'm able to connect to my Ubuntu system (*I get a "Unencrypted Connection" warning*), but I end up with a gray screen.

The "~/.vnc/xstartup" has been configured like this:
```
#!/bin/sh
# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
gnome-panel &
gnome-settings-daemon &
metacity &
nautilus &

```

My logs show this:
```

Xvnc Free Edition 4.1.1 - built Feb 25 2015 23:02:21
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc

Tue Jan 23 11:26:46 2018
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
XKB extension not present on :1
Error:            XKB extension not present on :1
                  Exiting
Starting session: /etc/X11/Xsession
Tue Jan 23 11:26:53 2018
 Connections: accepted: 0.0.0.0::56195
 SConnection: Client needs protocol version 3.8
 SConnection: Client requests security type VncAuth(2)
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 6 (8bpp) rgb222
 VNCSConnST:  Client pixel format depth 16 (16bpp) little-endian rgb565
Session terminated with return code 1
Tue Jan 23 11:26:56 2018
 Connections: closed: 0.0.0.0::56195 (Clean disconnection)
 SMsgWriter:  framebuffer updates 3
 SMsgWriter:    raw rects 1, bytes 16396
 SMsgWriter:    ZRLE rects 3, bytes 305
 SMsgWriter:    raw bytes equivalent 2375984, compression ratio 142.265972


```

VNC Viewer just displays a grey screen. I'm not sure what to do next?

---

### Post by TheFu on 2018-01-23
A gray screen is just an empty X-root window (desktop).  You probably need to start a Window Manager, then some sort of menu system and then an X/client.  See the "xsetroot -solid grey" in your startup?  That's the desktop you have.

Right click anywhere on the desktop, does a menu get displayed?

Unity probably won't work over any remote desktop.  It needs direct HW access to a GPU.  You want to use a lite environment, like XFCE, LXDE, or even Mate.  But ... there is a better option.

VNC is sorta slow. VNC isn't secure. If you want a faster, secure, remote desktop, check out x2go. It feels 2-3x faster than any VNC I've used.  It is based on the NX protocol, which includes ssh.  Don't use Unity. Use XFCE, LXDE, Mate or a plain Openbox environment.  Adding these is about 2 minutes.  Purge Unity. On a headless system, it is a liability.

---

### Post by drieske2 on 2018-01-23
Okay, thanks. I'll consider XFCE instead!

---

### Post by TheFu on 2018-01-23
> **drieske2 said:**
> Okay, thanks. I'll consider XFCE instead!

Using that isn't going to change the gray xsetroot at all.  You'll need to do more.

I'll ask again, does right-clicking on the desktop show a menu?

---

