---
title: "need help getting GeForce3 Ti 200 installed Dapper"
date: 2006-11-11
forum: General Help
---

### Post by J-Rod on 2006-11-11
I have tried following the wiki, and installed the nvidia-glx in synaptic. When I go to enable the driver from terminal, I get this message:

> Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
jrodder@jrodder-desktop:~$


On my first install I tried the command given there, and I was able then to run the sudo nvidia-glx-config enable command. This broke my X however, and not really knowing what to do from there without much headache, I reinstalled. Any input is greatly appreciated.

---

### Post by J-Rod on 2006-11-11
I just tried running Easy Ubuntu, and doesn't look like that worked either as far as enabling the 3d.

> jrodder@jrodder-desktop:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
jrodder@jrodder-desktop:~$


---

