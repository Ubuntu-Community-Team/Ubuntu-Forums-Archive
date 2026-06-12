---
title: "need help with 3D acceleration"
date: 2007-06-07
forum: General Help
---

### Post by nerdman978 on 2007-06-07
I want to get 3D acceleration working so 
1) I can play games
2) I can run beryl

I have tried the fglrx driver many, many times but it just doesn't work and my xserver breaks every time 
Here is what my terminal spits out:

> nate@nate-laptop:~$ glxinfo | grep direct
direct rendering: No

and this as well
> nate@nate-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2

And here is the device section of my xorg.conf 
> Section "Device"
	Identifier	"ATI Mobility Radeon 9000"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Any help is great.

---

### Post by Irony on 2007-06-07
At the risk of stating the obvious, have you tried;

[PHP]Section "Device"
Identifier "ATI Mobility Radeon 9000"
Driver "fglrx"
BusID "PCI:1:0:0"
EndSection[/PHP]

---

### Post by nerdman978 on 2007-06-07
yes but the xserver crashes every time and I either 
sudo dpkg-reconfigure xserver-xorg 
or
cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

which is a pain either way

---

### Post by nerdman978 on 2007-06-07
Woah! I just found this really kick@$$ app that I think all debian/ubuntu users should check out. It auto-detects your graphics card and then downloads and installs the right drivers for it! Get it here

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

I'll see if it works for me....

---

