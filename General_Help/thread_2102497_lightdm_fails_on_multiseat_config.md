---
title: "lightdm fails on multiseat config"
date: 2013-01-07
forum: General Help
---

### Post by zoltan_szecsei on 2013-01-07
Hi,
I'm struggling a bit setting up 2 seat multiseat on ubuntu 12.10.
/var/log/Xorg.0.log (and .1.log) show no errors but the "Server Terminates successfully".
/var/log/lightdm.log seems OK, as does the x-0.log and x-1.log.

**The x-0-greeter.log however contains:**
No protocol specified
No protocol specified
No protocol specified

** (unity-greeter:1726): WARNING **: Could not open X display
Activating service name='org.a11y.atspi.Registry'
No protocol specified

(unity-greeter:1726): Gtk-WARNING **: cannot open display: :0
No protocol specified
No protocol specified

** (at-spi2-registryd:1749): WARNING **: Could not open X display


I got the above info by SSH-ing into the multiseat box.
The main screen on the multiseat box says:

[I]The system is running in low-graphics mode.
Your screen card, graphics .... could not be autodetected.....[/I]


Please can someone point me in a direction to solve this.

**My /etc/lightdm/lightdm.conf file has:**
[Seat:0]
xserver-command=/usr/bin/X :0
xserver-config=xorg.conf
xserver-layout=seatTop

[Seat:1]
xserver-command=/usr/bin/X :1 -sharevts
xserver-config=xorg.conf
xserver-layout=seatMid
autologin-user=geograph
autologin-user-timeout=30



Thanks in advance,
Zoltan

---

### Post by Jezdec on 2013-11-20
Hi, I struggled with this on ubuntu 13.10. Through trial and error, I found that **/etc/lightdm/lightdm.conf** needs this:

> [Seat:0]
xserver-command=/usr/bin/X vt7

[Seat:1]
xserver-command=/usr/bin/X vt8


Also, there is no **xorg.conf **file, which doesn't seem to matter.

---

