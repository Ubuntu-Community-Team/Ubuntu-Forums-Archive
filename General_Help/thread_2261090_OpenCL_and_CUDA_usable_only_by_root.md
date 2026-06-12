---
title: "OpenCL and CUDA usable only by root"
date: 2015-01-16
forum: General Help
---

### Post by flix3 on 2015-01-16
Hello everybody.

I'm on Ubuntu 14.10 (64bit), and I'm using for my graphic card (GeForce GT 630), the recommended proprietary drivers (331.113).

The problem is the following:

I have no problems at all when running hardware accelerated OpenGL programs, except when OpenCL and CUDA must be used. In that case the following weird behaviour occurs:

1) After logging to Ubuntu, every time I have to run a program that is using OpenCL or CUDA, no platform is detected (I've tested it with both OpenCL and CUDA in various ways, and this can be easily tested by using the Blender3D program: under User Preferences, no Compute Device is detected).

2) However if I run the program with ***sudo***, then I can use OpenCL or CUDA again, and it works nice.

3) After that, if I run or re-run **every** program that uses OpenCL or CUDA normally (**without** being root), it keeps working.

4) But when I shutdown my PC and reboot, everything restarts from point 1.

Any advice or hint, please?

---

### Post by efflandt on 2015-01-16
I don't really know what OpenCL and CUDA are used for. But while trying to figure out how to report an issue with nvidia-346 from xorg-edgers ppa (never quite figured out who to contact) I stumbled on a bug report about things related to OpenCL and CUDA not having proper permissions for /dev files and one of the recommendations was to recommend **nvidia-modprobe** for various nvidia driver versions including versions in regular repos. I do not know how to quickly find that bug report at this time, but you might look at (or web search) **nvidia-modprobe** and see if it may help.

[http://packages.ubuntu.com/search?keywords=nvidia-modprobe](http://packages.ubuntu.com/search?keywords=nvidia-modprobe)

---

### Post by flix3 on 2015-01-17
Thanks for the tip,  				 				 					 						 	[**[COLOR=#000000]efflandt[/COLOR]**]("http://ubuntuforums.org/member.php?u=937632") :p.

Soon after having installed, via Synaptic, **nvidia-modprobe**, the problem disappeared.

---

