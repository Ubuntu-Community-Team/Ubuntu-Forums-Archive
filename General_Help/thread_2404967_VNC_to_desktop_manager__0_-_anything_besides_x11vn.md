---
title: "VNC to desktop manager / :0 - anything besides x11vnc??"
date: 2018-10-30
forum: General Help
---

### Post by treii28 on 2018-10-30
Are there any other vnc servers besides x11vnc that will allow ubuntu to use VNC to the system without creating a new session / using the existing console view?  Raspberry pi's can do it with jessie for goodness sake, why is this a problem for Ubuntu?

I generally use x11vnc to do this, but one of my boxes is triggering a known bug whenever a window/menu/popover/dialogue pops up which causes x11vnc to drop a stack smash and restart, disconnecting the session. X11vnc hasn't been updated since 2011 and is a wee big orphaned as of late 2018. It would be nice if there was another solution available out there vs. a 7 year old program.

SW

---

### Post by nlee2 on 2018-10-30
vino works for me.

---

### Post by treii28 on 2018-11-01
same session as console? From the login prompt? Or do you have to log in first before it's enabled/listening?

---

### Post by treii28 on 2018-11-01
lol, and vino is broken in 18.04 (no vino-preferences to be found anywhere! Yay!!!!)

I was able to manually disable it via dconf-editor and it's default configuration is installed as a user based service in systemd. Which means vino is not available until a user is logged into a session. Which means it doesn't work from console unless you have already logged in from console. This means if you haven't logged in locally or reboot the machine, vnc will NOT be running and you will NOT be able to remote connect to the machine's local console. So no, vino is not an alternative solution unless it is possible to get it to run from/with the desktop manager.

I'll leave it installed for the time being as if the bug in the orphaned x11vnc becomes annoying, I can ssh in, shut down x11vnc after I log in, and start vino-server as a user. But that is hardly an ideal solution (because it is frankly a pain in the ass).  C'mon ubuntu community - Raspberry pis are embarassing the crap out of you!  I just check a box on my default pi installs and it's working out of the box! Regardless if I'm logged in or not, regardless of the desktop manager, regardless of the session manager, regardless if I have set up auto-login.

SW

---

### Post by nlee2 on 2018-11-01
I have my vino user with auto-login and autostart of vino-server.

Put this in ~/.config/autostart/vino-server.desktop or in the GUI it is Settings --> Sharing

```
[Desktop Entry]
Type=Application
Exec=/usr/lib/vino/vino-server
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=vino
Comment=

```

---

### Post by Adrian_Padilla on 2018-11-01
im pretty sure you can use Teamviewer 

[https://www.teamviewer.com/en-us/download/linux/](https://www.teamviewer.com/en-us/download/linux/)

---

