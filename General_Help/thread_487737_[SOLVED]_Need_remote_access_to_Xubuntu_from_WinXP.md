---
title: "[SOLVED] Need remote access to Xubuntu from WinXP"
date: 2007-06-29
forum: General Help
---

### Post by beengone on 2007-06-29
I am setting up an old laptop with Xubuntu for my grandparents.  I know when I give it to them they'll have lots of questions.  I need to be able to help trouble-shoot and walk them through things from my Windows XP machines.  It looks like Xubuntu doesn't come with any sort of VNC client or anything.  I searched through these forums and didn't find anything useful. 

So, can someone give me a rundown of how I install some sort of app that will always run and through which I may attach to the laptop via IP and log in through my admin account?  Then, what do I need to install on my Windows boxes?

Here may be a catch:  I'm new to Linux and prefer some sort of graphic setup on both ends if possible.  If I have to install and set up from the terminal, I can, but will need a little extra hand-holding.

Thanks
Dan J.

---

### Post by tvst on 2007-06-29
> **beengone said:**
> It looks like Xubuntu doesn't come with any sort of VNC client or anything.

you can install a vnc server by searching for "vnc4server" (without quotes) using synaptic, or typing the following on the terminal:

```
sudo apt-get install vnc4server
```

see this thread for more info:
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

---

### Post by Pheodax on 2007-06-29
And install TightVNC on your Windows XP box to access the Xubuntu VNC server. It's fast and free.

---

### Post by beengone on 2007-06-29
All those instructions seem to be for a different release or something, but I figured out how to get it installed.  But, I went through step 4 and came out with errors. 

Running Xubuntu 7

for step 4:
Add vnc service to xinetd:
Code: sudo gedit /etc/xinetd.d/Xvnc

I get errors.

Warning: unknown mime-type for "/etc/xinetd.d/Xvnc" - - using "application/*"
Error: now write permission for file "/etc/xinetd.d/Xvnc"


Any idea how to fix this?

---

### Post by beengone on 2007-07-06
I do not think VNCserver is running on my Linux box.  It's installed, but the setup doesn't seem to be complete.  I downloaded and installed VNCserver, but don't think it is set up all the way and running.  I need to keep it running at all times so I can access this machine when my grandparents have trouble. 

Can someone walk me through this?

Thanks
Dan J.

---

### Post by jinx099 on 2007-07-06
What is the output of:

```

vncserver

```

or 

```

vnc4server

```

---

### Post by beengone on 2007-07-09
This time around it's different:

I get

You will require a password to access your desktops.

usage: vncpassword [passwdFile]


To me, it looks like it's running, right?  But, when I try to access the IP address via TightVNC viewer, I get

Failed to connect to server (IP ADDRESS)

Dan J.

EDIT:  I seem to have created a password and now have what seems to be a working vncserver, but still get the same error when I try to access it via IP...

---

### Post by beengone on 2007-07-11
I got in using tightVNC.  When I connected, I just got a terminal windows.  This isn't useful for me.  I need to be able to see exactly what the user on the other ends sees (the desktop, etc).  Is this possible?  I'm looking for something like Remote Desktop or DameWare.  Does vnc4server/tightvnc do this?

Thanks

---

### Post by beengone on 2007-07-11
I found this on another forum, but don't know how to edit xstartup, can someone hold my hand through this:

In case any one else is struggling to get XFCE desktop working with VNC I offer the following suggestions.

Make sure that your xstartup file has “& xfwm4 & xfce4-panel &” in it.

Without the xfce4-panel included I just get a terminal window. Which was fine for a while, but I certainly prefer to have the whole panel.

---

### Post by beengone on 2007-07-13
*Edits for 7.10 / VNC4SERVER below*

Got it!   In case anyone wants to do this running Feisty Xubuntu and vnc4server:

edit the file /etc/vnc/xstartup to look like this:

#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &

# twm &

xfwm4 --display :1.0 &
xfce4-panel --display :1.0 &
xfdesktop --display :1.0 &



Next, start the server session like so:

vnc4server -extension XFIXES -depth 24 -geometry 1024x768


That should get you up and running with xfce/vnc4server.  I connected via tightvnc and it all works perfectly.

Dan J.


NOTE:  Running 7.10 with VNC4SERVER installed, the location of xstartup is /home/user/.vnc/    - - -   accordingly, change the instructions above to indicate "$HOME/.vnc/xstartup"

---

### Post by redcharlie on 2007-07-16
Yes, I have this issue as well.
It's quite an irritant, especially considering that xfce is ideal for use with VNC.  With 6.06 I was able to use vnc as long as I started my VNC server *before* loging on via gdm.  Otherwise the session manager would crash and other unpleasantness would happen.  But since this in on a server, and I rarely logon locally (via gdm) this wasn't such a problem once I got around the catch-22 of the situation. i.e. vnc would work, as long as I hadn't already logged on locally via gdm, but since at first I didn't know that, I remained logged on via gdm while I tried to get VNC to work!! >:-O  

for me, instead of starting each component (xfwm, xfce4-panel, xfdesktop, etc.) I just invoke "startxfce4" at the bottom of my ~/.vnc/xstartup script

(I also have a line:
export VNCSESSION=TRUE
near the top of ~/.vnc/xstartup
so that /etc/xdg/xfce4/xinitrc doesn't try to start a screensaver for my vnc display! )

but the real trick is the "-extensions XFIXES" option.  It's a crude hack, see
[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/78887](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/78887)

but it works!!
(...somebody fix this for real, please!)

---

### Post by martyh99 on 2007-08-26
> **beengone said:**
> Got it!   In case anyone wants to do this running Feisty Xubuntu and vnc4server:

edit the file /etc/vnc/xstartup to look like this:

#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &

# twm &

xfwm4 --display :1.0 &
xfce4-panel --display :1.0 &
xfdesktop --display :1.0 &

Next, start the server session like so:

vnc4server -extension XFIXES -depth 24 -geometry 1024x768

That should get you up and running with xfce/vnc4server.  I connected via tightvnc and it all works perfectly.

Dan J.

Thank you very much for posting this fix work around. It worked for me too.
But I noticed that this only works when I am actually login in locally to the my machine. If I am not logged in to my machine, the remote VNC client from the other machine only sees a grey screen and not the taskbar, panel, et. al.
Is there something I still need to do so that the remote machine sees the full panel, even when I am not logged on the local machine - am I missing something?
Thanks in advanced.

---

### Post by beengone on 2007-11-26
Unfortunately, I'm a beginner.  I had a friend help me since these forums offered little hand-holding, which is what I needed.  I would also like this solved though.  Maybe someone will comment?....

---

### Post by beengone on 2007-11-26
please see notes a few posts up about a new location for xstartup.  Also, here is a link I used to get 7.10 working:

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

---

