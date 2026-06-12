---
title: "Connect to Ubuntu VNC Server Fails"
date: 2007-10-31
forum: General Help
---

### Post by bumcheekcity on 2007-10-31
I have set up a VNC server on my Ubuntu box, and I'm trying to connect to it via my Windows box, not on the same LAN. The Ubuntu box is directly connected to the internet, running as my home server (I'm at uni).

Whatever VNC client I use, I type in my home IP 123.456.789.0, and it wont connect at all, and times out with a 10060 error. I have to explicitly type 123.456.789.0:5901 to get it to come up with anything.

If I DO explicitly specify the port, then my VNC client wont allow me to type in the username, just the password, and whatever I type in, fails to connect. Encryption is turned off for my VNC server (I just left it on default). Can anyone suggest how I can solve this? I only have SSH access to my box, so Terminal commands only, please :D

Sidenote: Connecting to 123.456.789.0:5901 in my browser yields the text "RFB 003.008", and nothing else. Maybe that's helpful.

---

### Post by troyer81 on 2007-10-31
There are several HOWTOs about how to setup VNC Servers for Ubuntu.  Here's a link to one of them:

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

In general, the piece I think you are missing is that the VNC service runs with a "universal" password to even connect to the VNC service.  Your VNC client will prompt for that password first (set via the "sudo vncpasswd /root/.vncpasswd" command in the HOWTO).  Once you have given the password to connect, you then deal with the actual logon to the system with a username and password for Ubuntu (assuming the "instance" that you are connecting to hasn't already been logged in).

I know that doesn't completely answer your question, but it might send you in the right direction.

Also, FYI, the reason you probably have to explicitly set the port to 5901 is that the default is port 5900.  You could also send the same port change by setting the IP to something like this:  123.456.789.0:1

:1 = 5901, :2=5902, etc...

If you follow the HOWTO, 5900 is not the correct port, so the default (i.e. no "colon" after the ip) doesn't work.

I hope that helps a little....

---

### Post by bumcheekcity on 2007-11-01
> Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Fri Jul 20 08:38:43 2007
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
/home/andreas/.vnc/xstartup: 12: twm: not found
ICE default IO error handler doing an exit(), pid = 5907, errno = 0
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.

I dont MIND having to explicitly specify the port, now that I know I'm using a non-standard one, that's OK. I've set the universal password, and typed it in, and still nothing happened, I just got a "connection closed unexpectedly" error. I enclose the ubuntuserver:1.log file in my .vnc folder above.

I thought it might be because there was no desktoip manager installed, so I installed xubuntu-desktop, but that didn't do anything, and now it doesnt even ask me for the password before giving me the error.

---

### Post by eldragon on 2007-11-01
your vnc server is running at port 5901, thats your problem...

here's how i do it. and it can be set up through ssh ;)
[http://ubuntuforums.org/showthread.php?p=3554778#post3554778](http://ubuntuforums.org/showthread.php?p=3554778#post3554778)

just remember to sudo /etc/init.d/gdm restart to get the server up and running....
or just run the script through ssh :D

---

### Post by bumcheekcity on 2007-11-02
Ah, an embarassing problem, I has to start the program "vncserver"... yeah...

But now, I can connect and authenticate, but there's no X Server, so I type "startx" and I get:

> user not authorized to run the X server, aborting.

So I type "sudo startx" and I get:

> Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

giving up.
xinit:  unable to connect to X server
xinit:  No such process (errno 3):  unexpected signal 2.
xauth:  error in locking authority file /home/andreas/.Xauthority


Any suggestiong on how I can get VNC to open up X?

---

### Post by Dragon45 on 2007-12-20
I saw this fix on a mailing list, and it worked for me:

Delete ```
/home/myName/.Xauthority
``` it may have become a 'stale' file due to a system crash or something else bizarre. Apparently it can be dynamically regenerated if it needs to be.

---

