---
title: "3ddesk"
date: 2005-07-07
forum: General Help
---

### Post by JumpyLINUX on 2005-07-07
When I try to run 3ddesk I get the following error:

```

Attempting to start 3ddesktop server.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

``` 

What should I do?

---

### Post by Lord Illidan on 2005-07-07
I think you need open gl..first, is your graphics card nvidia? If so get the drivers for NVIDIA from Synaptic..and while you are there see if there are other packages for open gl, which you might have missed.

---

### Post by JumpyLINUX on 2005-07-07
I have nvidia-glx and nvidia-settings adn nvidia-kernel-common.

My graphics card is GeForce4 Ti 4200.

---

### Post by Lord Illidan on 2005-07-07
Ah, good, but is nvidia enabled in your xorg.conf?

Try going to the xorg.conf (sudo vi /etc/X11/xorg.conf)..

And in Section Device (which should look like this)  : 

Section "Device"
	Identifier	"GeForce4 Ti 4200."
	Driver		 "nv"
	BusID		"PCI:1:0:0"
EndSection

change nv to nvidia...

Exit vi and restart the x-server...

It should work now..

---

### Post by casper26 on 2006-03-12
Thank you!!  It worked perfectly! Nice job!!

---

### Post by JungleBeast on 2006-04-28
Hey there, I have a similar problem, but under Section Device I have:

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9600 (RV350 AS)"
        Driver          "ati"
        BusID           "PCI:1:0:0"

Any ideas?

---

### Post by JungleBeast on 2006-05-03
anyone?

---

### Post by mobasher_helmy on 2007-03-09
maybe you can refer to this thread....i hope it helps you cuz it helped me 

[http://ubuntuforums.org/showthread.php?t=292642&highlight=XFree86-DRI+missing+on+display+0%3A0](http://ubuntuforums.org/showthread.php?t=292642&highlight=XFree86-DRI+missing+on+display+0%3A0)

---

