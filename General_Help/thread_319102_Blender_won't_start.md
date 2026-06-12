---
title: "Blender won't start"
date: 2006-12-15
forum: General Help
---

### Post by jeremy on 2006-12-15
Just installed blender from the edgy repos, and it won't start.
When I tried from a console, this is what I got:

jeremy@work:~$ blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.4.
Checking for installed Python... got it!
libGL warning: 3D driver claims to not support visual 0x4b

and it just stopped there.

Any ideas?

---

### Post by xopher on 2006-12-15
Make sure you have 3D enabled with your graphic drivers.

```
glxinfo | grep rendering
```

^ Should say: Rendering: Yes

---

### Post by jeremy on 2006-12-15
Thanks, but i just get the same message:

jeremy@work:~$ glxinfo | grep rendering
libGL warning: 3D driver claims to not support visual 0x4b

Here is the relevant section from xorg.conf

Section "Device"
	Identifier	"Matrox Graphics, Inc. MGA G550 AGP"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	Option		"OldDmaInit"		"True"
EndSection

---

### Post by xopher on 2006-12-15
This bug may be what you are experiencing:

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-mga/+bug/58721](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-mga/+bug/58721)

And here's a proposed workaround from the same page:

> 

I have found a workarround to use the `mga' driver again: I activated the kernel framebuffer interface in the device section of the X.org configuration file /etc/X11/xorg.conf (Option "UseFBDev" "true").

Section "Device"
        Identifier "Matrox Graphics, Inc. MGA G200"
        Driver "mga"
        BusID "PCI:1:6:0"
        Option "UseFBDev" "true"
        Option "OldDmaInit" "True"
EndSection

I haven't tested it with the default ubuntu kernel, but with my self-compiled 2.6.18-rc6, I had to load the `matroxfb_base' before starting the X-Server. If you compile the matrox framebuffer into the kernel, you shouldn't notice any problems. If you have compiled it as a module, you should add `matroxfb_base' to your /etc/modules file.


And here seems to be a backported fix for it [i386]:
[http://buntudot.org/people/~jdong/backports/edgy/58721/xserver-xorg-video-mga_1.4.4.dfsg.1-1jdong1~6.10prevu1_i386.deb](http://buntudot.org/people/~jdong/backports/edgy/58721/xserver-xorg-video-mga_1.4.4.dfsg.1-1jdong1~6.10prevu1_i386.deb)

---

### Post by jeremy on 2006-12-15
[http://buntudot.org/people/~jdong/backports/edgy/58721/xserver-xorg-video-mga_1.4.4.dfsg.1-1jdong1~6.10prevu1_i386.deb](http://buntudot.org/people/~jdong/backports/edgy/58721/xserver-xorg-video-mga_1.4.4.dfsg.1-1jdong1~6.10prevu1_i386.deb)
did the trick, thank you very much for your help.

---

