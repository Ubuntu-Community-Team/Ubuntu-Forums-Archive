---
title: "VNC not working on VPS, Log in question."
date: 2017-01-24
forum: General Help
---

### Post by bi2te3powered on 2017-01-24
Hey Everybody,
Thanks in advance for the help.
I'm relatively weak with Linux, and this is part of my learning process, so bear with me if this a dumb question. I am trying to get VNC running on my Ubuntu 16.04 VPS. I have tried multiple VNC server software options. The closest I have gotten to success to far is vnc4server. I have been able to get it to produce a log file. So here it is:


```

Xvnc Free Edition 4.1.1 - built Feb 25 2015 23:02:21
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc




Tue Jan 24 19:04:38 2017
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5905
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/Type1/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  8 (RRGetScreenResources)
  Serial number of failed request:  31
  Current serial number in output stream:  31
Failed to parse arguments: Unknown option --login

```
I'd love to get this working so I am not relegated to the command line. As much as it is a good thing to force myself, I think I can do so much more if I have GUI access.

---

### Post by steeldriver on 2017-01-24
Hello and welcome to the forums

Can you summarize the steps you took to get to that point - in particular how you started the vncserver, and the contents of the invoking user's ~/.vnc/xstartup file?

---

### Post by bi2te3powered on 2017-01-24
The short answer to the steps question is that I just ran the command *vnc4server.* The long answer would take all day to type up.

xstartup as follows:
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



```

---

### Post by Elishasmantle on 2017-05-29
Hello,

I had massive issues as a noob to linux and getting vncserver setup.

This is the best post I found so far for installing and getting vncserver to work.

I did decide to delete my vps install and start fresh because 1: I am new to linux and 2: I had tried so many forum suggestions I was afraid I might have messed up a config file somewhere or have a clash with software.

[https://www.howtoforge.com/tutorial/ubuntu-gnome-vnc-headless-server/](https://www.howtoforge.com/tutorial/ubuntu-gnome-vnc-headless-server/)

I used almost the whole article, except windows informational steps and it worked.

---

