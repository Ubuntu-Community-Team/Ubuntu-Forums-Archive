---
title: "X.org / DRI / Radeon support."
date: 2004-11-21
forum: General Help
---

### Post by mkools on 2004-11-21
Ok, all night I tried and tried but no luck in getting it to work decent :)

I installed the latest DRI snapshots for my radeoncard from:

[http://www.freedesktop.org/dri/snapshots/](http://www.freedesktop.org/dri/snapshots/)

...and installed them without any errors.

I created a new file in /etc/modutils named 'radeon' and entered the info:

pre-install radeon /sbin/modprobe -k agpgart

I started update-modules after that.

I'm using a 2.6.9 kernel with agpgart compiled as module.

When I reboot my system, lsmod display's:

ndiswrapper           108304  0
nvidia_agp              6044  1
agpgart                28456  2 nvidia_agp
sk98lin               167144  1

So as you can see my agpmodules are loaded ok, but I can't see the DRI
module.

When I do a modprobe radeon, lsmod says:

radeon                131744  2
ndiswrapper           108304  0
nvidia_agp              6044  1
agpgart                28456  2 nvidia_agp
sk98lin               167144  1

so it's loaded at this time.

Now when I start xorg and check my DRI support it says:

# glxinfo | grep direct
direct rendering: Yes

So that should be ok I guess but things that use DRI are pretty slow,
so I did a glxinfo | grep Mesa:

OpenGL renderer string: Mesa DRI R200 20030328 AGP 1x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 6.1

As you can see I have DRI support but with some slow Mesa DRI driver which runs
at agp 1x.

Any thoughts on how I can fix this?

Thanks in advance!

---

### Post by wongk on 2006-11-27
The composite extension is enabled by default in edgy.  The ATI driver does not support the composite extension, and when it is turned on it disables DRI.  Try adding the following to the end of /etc/X11/xorg.conf:

Section "Extensions"
    Option "Composite" "false"
EndSection

Then press Ctrl+Alt+Backspace to reboot your X server.

---

