---
title: "HOWTO: Lubuntu VNC server installation in Saucy 13.10"
date: 2013-12-11
forum: General Help
---

### Post by s-stefanov on 2013-12-11
After reading 10 000 guides suggesting that pretty much any VNC server should run in Lubuntu I faced issues runnning any of them and getting a proper desktop environment. RealVNC, x11vnc, tightvncserver, and vino were the candidates. I ended up using tightvncserver. The way to get it working is:

1) Install the package with:

```
sudo apt-get install tightvncserver autocutsel
```

2) Run the server once and kill it:

```
tightvncserver :1
tightvncserver -kill :1
```

3) This will create a ~/.vnc/xstartup file. Modify it like this:

```
##xrdb $HOME/.Xresources
#/etc/X11/Xsession
autocutsel -fork
openbox &
/usr/bin/lxsession -s Lubuntu -e LXDE &
```

The tricky part was the openbox window manager. All guides seem to skip it, I found it by pure luck here:

[HTML]http://www.madebits.com/blog/comments.php?y=12&m=06&entry=entry120617-014832[/HTML]

It also works if you comment out the existing entry for X Window Manager instead adding openbox:

```
#x-window-manager $
```

You also need to add the following line in order to get bidirectional clipboard sharing

```
autocutsel -fork
```

4) Final config looks like this:

```
#!/bin/sh

#xrdb $HOME/.Xresources
xsetroot -solid grey

#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &

export XKL_XMODMAP_DISABLE=1
autocutsel -fork
openbox &
/usr/bin/lxsession -s Lubuntu -e LXDE &
```

5) Use the vnc server as normal:

```
tightvncserver :1
```

It tends to throw some errors in the log files but I didn't bother to investigate much as it works:

```
11/12/13 13:00:43 Xvnc version TightVNC-1.3.9
11/12/13 13:00:43 Copyright (C) 2000-2007 TightVNC Group
11/12/13 13:00:43 Copyright (C) 1999 AT&T Laboratories Cambridge
11/12/13 13:00:43 All Rights Reserved.
11/12/13 13:00:43 See http://www.tightvnc.com/ for information on TightVNC
11/12/13 13:00:43 Desktop name 'X' (Server:1)
11/12/13 13:00:43 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
11/12/13 13:00:43 Listening for VNC connections on TCP port 5904
Font directory '/usr/share/fonts/X11/Type1/' not found - ignoring
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
** Message: main.vala:96: Session is Lubuntu
** Message: main.vala:97: DE is LXDE
Obt-Message: XKB extension is not present on the server or too old
Obt-Message: Xinerama extension is not present on the server
Obt-Message: XRandR extension is not present on the server
Xlib:  extension "RANDR" missing on display ":1".
** Message: main.vala:128: log directory: /home/<user>/.cache/lxsession/Lubuntu
** Message: main.vala:129: log path: /home/<user>/.cache/lxsession/Lubuntu/run.log
Xlib:  extension "XInputExtension" missing on display ":1".
Xlib:  extension "XInputExtension" missing on display ":1".
Openbox-Message: Requested key "Print" does not exist on the display
Openbox-Message: Requested key "Print" does not exist on the display
Openbox-Message: Unable to find a valid menu file "/var/lib/openbox/debian-menu.xml"
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"
      after 1496 requests (1496 known processed) with 0 events remaining.
```

P.S. Any clue why vBulletin forum software adds an extra blank row at every [CODE] section? I'm closing the tag exactly after the last character typed.

EDIT 1: Modified to include clipboard sharing.

---

### Post by ABitTooSpicy on 2013-12-16
Just followed your instructions and everything was going well. Then I noticed that any apps I open in the VNC viewer window open, but don't display in the viewer. Instead show up on the server machine's desktop... any idea what could be causing this?

***EDIT***
Ok never mind, it's only happening for some applications. Like Chrome. Wonder what is different between firefox / terminal (which work as expected) and chrome which doesn't display on the remote machine running vncviewer.

***EDIT 2***
Ok really never mind now. Chrome was already running on the desktop so any windows i opened via the vncviewer continued to open on the same session. If I close chrome completely on the server, any subsequent chrome windows on the viewer showed in the viewer as expected. (seems quite silly once you figure it out!!) =)

---

### Post by s-stefanov on 2013-12-16
> **ABitTooSpicy said:**
> Just followed your instructions and everything was going well. Then I noticed that any apps I open in the VNC viewer window open, but don't display in the viewer. Instead show up on the server machine's desktop... any idea what could be causing this?

***EDIT***
Ok never mind, it's only happening for some applications. Like Chrome. Wonder what is different between firefox / terminal (which work as expected) and chrome which doesn't display on the remote machine running vncviewer.

In order to get control of the physical console in my experience you need to run a VNC server from within the desktop manager. I've managed to achieve it with RealVNC and GDM but I haven't tried LightDM. Maybe you have done something like this?

As a side note - running TightVNC in the abovementioned setup leads to unencrypted password authentication. I'm personally tunneling VNC over SSH with something like this (executed on the client):

```
ssh <server> -L 5901/127.0.0.1/5901
vncviewer localhost:1
```

This way you get 2 benefits - open only a single port on the server for both SSH, SCP, and VNC + getting your VNC session secured.

---

### Post by joshuc on 2014-03-07
Well, I've configured my router to forward 5901 to my lubuntu server.
Can't seem to get a connection.

Just getting 'Connection refused: connect()'

I don't have any firewall rules.

Hmm

---

### Post by s-stefanov on 2014-03-08
You shouldn't open 5901 on the server, 22 (or whatever you use for SSH) is sufficient. You need to tunnel the VNC session over SSH otherwise traffic is sent cleartext. See my previous post about SSH tunnelling.

---

