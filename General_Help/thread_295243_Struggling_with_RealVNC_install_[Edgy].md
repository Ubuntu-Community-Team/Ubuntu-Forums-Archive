---
title: "Struggling with RealVNC install [Edgy]"
date: 2006-11-07
forum: General Help
---

### Post by eagle63 on 2006-11-07
Hey guys, I've got a fresh Edgy install and I'm working on getting VNC going.  I actually initially installed tightvnc using Synaptic, but I ended up removing it because the performance wasn't great and a co-worker suggested I try realvnc.  

So anyway, I downloaded the realvnc .tar file from the website, and did the ./vncinstall to /usr/local/bin per the README.  However, when I start vncserver, it never actually starts and leaves this error in the log:
```

Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'

Xvnc Free Edition 4.1.2 - built May 12 2006 17:42:24
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40201000, The XFree86 Project, Inc

Tue Nov  7 03:59:34 2006
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /usr/X11R6/lib/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from l
ist!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from
 list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from
list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from li
st!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from
list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from
 list!

Fatal server error:
could not open default font 'fixed'
xrdb: Connection refused
xrdb: Can't open display 'abrekken-ubuntu:1'
xsetroot:  unable to open display 'abrekken-ubuntu:1'

(gnome-session:4763): Gtk-WARNING **: cannot open display:

(gnome-terminal:4762): Gtk-WARNING **: cannot open display:

```

I have no idea why I'm getting these errors or what they mean.  Like I said, tightvnc was working so I don't know what's different about realvnc.  (other than I have to install this one manually)

Thanks for any ideas!!

---

### Post by garretwp on 2006-11-07
I know this is not a solution to your actual problem, but you might want to look into freenx! If you are concerned about performance, then freenx is the way to go. The performance is very good and you will not be disappointed!

- Garrett

---

### Post by eagle63 on 2006-11-07
Yeah, I've actually used freenx before and it's great except it doesn't support dual-monitors.  I connect a 20" monitor to my laptop, and view my ubuntu-box via VNC on the 20".  FreeNX won't "scale-up" to fit the screen but VNC will.  

Once FreeNX supports that I'll happily use it again.

---

### Post by garretwp on 2006-11-07
Hmmm, I am running twinview on my system at home. I do not see why freenx would not allow you to run on one screen and do your normal stuff on another.

- Garrett

---

### Post by eagle63 on 2006-11-08
I should have explained better.  It's not that you can't use freenx on a second monitor, it's that freenx isn't "dual-monitor aware" like most VNC clients are.  Example:

My windows laptop has a 14" screen.  It's connected to a 20" LCD monitor. I "extend my windows desktop" onto that 20" LCD. I want to connect to Ubuntu from my laptop, and view it on the 20" monitor.  With VNC, I can set the screen geometry to the resolution of the 20" and it will scale to fit the entire screen.
But with freenx, it refuses to fill the full 20" screen - even when I specify the correct resolution. I can still drag the freenx window onto the 20", but it doesn't fill the screen which is annoying to me.  

I actually talked to a support/engineer guy at NoMachine who claimed that they were working on this for their next major release.

---

### Post by tmastran on 2006-11-08
I used this tutorial on both dapper and edgy. When it came to edgy vnc would not start because the font path was backwards in my 
xinetd command and in xorg.conf. Once I fixed that it worked.

Make sure you use /usr/share/X11/fonts not /usr/share/fonts/X11

[http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc+resumable](http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc+resumable)

---

