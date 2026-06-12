---
title: "No desktop showing in Ubuntu 13.04 via VNC on a VPS .."
date: 2013-08-10
forum: General Help
---

### Post by ahmadka on 2013-08-10
Hi guys ... I have a VPS on which till now I've been using ubuntu 11.04 ... This OS is very outdated now, so I decided to give 13.04 a shot ...

So I've just installed Ubuntu 13.04 on my VPS ... After installation, I connected via putty as root, and ran the following commands exactly:

To update the repository:

```
apt-get update
```

To install the desktop version:

```
apt-get install ubuntu-desktop
apt-get install gnome-session-fallback
```

Setting up VNC server:

```
apt-get install tightvncserver
vncserver :1 -geometry 1280x960 -depth 16 -pixelformat rgb565
(then set the password when prompted)
```

Next I rebooted the VPS ..

After that, again via putty, I edited the xstartup file ...

```
vi ~/.vnc/xstartup
```

... and added this at the end ..

```
gnome-session &
```

... so that my xstartup file looks like this:

```
#!/bin/sh


xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
gnome-session &
```

Again I rebooted the VPS, initiated VNC server, and tried connecting via the VNC, and I get this:

[IMG]http://i.imgur.com/ZvzT8ii.jpg[/IMG]

I CAN create folders and stuff on the desktop, but there's not unity or gnome or anything like this ..

I then tried modifying my xstartup file to this (changed the last 2 lines):

```
#!/bin/sh


xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession --session=2d-gnome &
```

Again, I restarted, initiated VNC, and connected, and now I got this:


[IMG]http://i.imgur.com/a4VZp3i.jpg[/IMG]

When I press Okay, it goes back to the state shown in the first screen ..


So how do I fix this .. ? How do I get a proper desktop ?? :(

I would prefer trying out Unity, but I can stick with GNOME as well if needed ..

For now, I just want to get to my desktop again .. :(

---

### Post by dkbame-aa on 2013-09-24
I have the exact same problem atm can anyone help?

---

### Post by dkbame-aa on 2013-09-25
Anyone?

---

### Post by u571kills on 2013-09-25
This worked for me. 


```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
 unset SESSION_MANAGER
 unset DBUS_SESSION_BUS_ADDRESS
# exec /etc/X11/xinit/xinitrc
gnome-session-fallback &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
```

PS:I used the "native" vnc server. 
```
apt-get install vnc4server
```

---

