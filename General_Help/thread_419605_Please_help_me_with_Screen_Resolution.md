---
title: "Please help me with Screen Resolution"
date: 2007-04-23
forum: General Help
---

### Post by chris99 on 2007-04-23
Hi there, I'm very new to Linux, I've tried out a couple of distros, and want to make sure I can get stuff to work before I install it on my hard drive.
At the moment, the only screen resolution available is 640 by 480, and 60Hz.
I think I either have to install drivers or edit xorg.conf I don't know how to log in as root etc, so I would appreciate any help that is clear and simple.

My hardware:

Intel DG965WH Motherboard with Intel GMA X3000 onboard graphics (Intel has released open source drivers for these)

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

[http://www.intel.com/products/motherboard/DG965WH/index.htm](http://www.intel.com/products/motherboard/DG965WH/index.htm)

and my monitor is a Samsung SyncMaster 753DFX

[http://www.samsung.com/au/products/monitors/crt/syncmaster753DFX.asp](http://www.samsung.com/au/products/monitors/crt/syncmaster753DFX.asp)

Please explain simply, as I'm not very experienced. Thanks!

---

### Post by tommcd on 2007-04-23
After you install ubuntu you can go to applications>accesories>terminal and type:
"sudo dpkg-reconfigure xserver-xorg" (without quotes) to change your screen resolutions to what you want if the installer does not give the ones you want.  I think you can run this from the live CD also. Try it, it won't install anything on your hard drive.
To open xorg.conf, from the same terminal type "sudo gedit /etc/X11/xorg.conf". Go down to the screen resolutions section and put the resolutions you want first in each line before the others. This never works for me though, even after installing. The dpkg-reconfigure method does though.
And welcome to theforums!
EDIT: It has been a while since I did anything with the live CD. You may or may not need sudo before the commands. If it don't work without sudo, then use it.

---

