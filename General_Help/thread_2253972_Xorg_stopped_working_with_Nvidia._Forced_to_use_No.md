---
title: "Xorg stopped working with Nvidia. Forced to use Nouveau"
date: 2014-11-24
forum: General Help
---

### Post by BlackoutWorm on 2014-11-24
Hello. I have no idea how and why this happened because I rarely turn off the computer.
So this could have happened days ago.
Anyway. I have tried everything from reconfigure xorg, purging and reinstalling nvidia and xorg. But nothing Xorg still won't work.
So now I'm using Nouveau and the screen resolution is terribly low. Everything is so zoomed in.
I was thinking maybe my graphics card is dead, but Driver-manager is suggesting nvidia drivers, so I don't think so.
Would be great to clarify though. That way I can go buy myself a new Nvidia GeForce card. Although I hope that's not the case.
Please help me.
Thanks a lot in advance :)

---

### Post by BlackoutWorm on 2014-11-24
Edit
I found the graphics card in lshw, so I don't think it's dead.
Still not able to fix this.
Please help.

---

### Post by ajgreeny on 2014-11-24
So, come on, tell us. What nvidia card is it?  Has there been a recent update of nvidia-current or whichever package you were using, which may now be causing this problem?

It's impossible to help without that info.

---

### Post by grahammechanical on 2014-11-24
Are you really using Nouveau? It could be llvmpipe. It is still open source but it uses software rendering of 3D graphics. Ubuntu uses llvmpipe (a) when the graphic card cannot do hardware rendering of accelerated 3D graphics; (b) when we use the resume option in recovery mode; (c) and when there is an issue with a proprietary video driver.

If the details page says Gallium 0.4, then on Nvidia cards the driver is Nouveau. If it says Gallium 0.4 llvmpipe, then it is, well, it is llvmpipe. You can try setting Nouveau or another proprietary video driver in Additional drivers.

But think of this, if the graphic card was well an truly dead then Ubuntu would not be loading to a desktop. You might be loading to a Linux command line using the video mode set by the BIOS but I do not think that the loading of Ubuntu would get as far as the desktop.

[https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D)

Regards.

---

