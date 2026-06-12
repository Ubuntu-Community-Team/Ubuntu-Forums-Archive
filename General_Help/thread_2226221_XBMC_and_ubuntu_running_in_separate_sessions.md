---
title: "XBMC and ubuntu running in separate sessions"
date: 2014-05-26
forum: General Help
---

### Post by nonsense.junk on 2014-05-26
I have a linux box with Ubuntu 14.04 running with Mythtv backend and xbmc frontend.  I have mythtv frontend installed (but not running) to control my pvr features.  I have my system setup to autologin to xbmc.  I have it to autostart x11vnc in display :0.


I wanted to know if it's possible to have xbmc in one session (tty7) and ubuntu in another session (tty8).  I want to be able to vnc into the xbmc session with display :0 and vnc into the ubuntu session with display :1.  Anyone have anything running like this?


Here is my lightdm.conf in my attempt to do this but it doesn't work.  I just go the login to xbmc and vnc into that session.


```
[LightDM]
seats=Seat:0 Seat:1


[SeatDefaults]
autologin-guest=false
greeter-session=unity-greeter
user-session=XBMC
#xserver-allow-tcp=true
autologin-user-timeout=0




[Seat:0]
autologin-user=htpc
user-session=XBMC
greeter-hide-users=true
autologin-session=XBMC-autologin
#allow-guest=false
display-setup-script=x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -alwaysshared -bg -rfbauth /etc/x11vnc.pass -rfbport 5900


[Seat:1]
user-session=ubuntu
autologin-session=ubuntu-autologin
autologin-user=htpc
greeter-session=unity-greeter
display-setup-script=x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :1 -auth /var/run/lightdm/root/:0 -forever -alwaysshared -bg -rfbauth /etc/x11vnc.pass -rfbport 5901
vt=8

```

---

### Post by matt_symes on 2014-05-26
Hi

You can start another x session easily enough.

I start xmbc on tty8 while running xfce on tty7 by dropping to tty0 and typing

xinit /usr/bin/xbmc -- :1

Switch between them in the usual way. I don`t use vnc though

Kind regards

---

