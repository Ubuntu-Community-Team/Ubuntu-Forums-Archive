---
title: "Entire display is shifted downwards off monitor slightly in native resolution"
date: 2019-02-28
forum: General Help
---

### Post by nlane515 on 2019-02-28
I have a black bar at the top of my screen, but only in the native resolution of my monitor(1440x900x75hz[16:10]). Any other resolution and the black bar goes away, but all other selectable resolutions in settings are in the 5:4 aspect ratio, and the screen gets fuzzy. I considered reinstalling Ubuntu 18.04(what I'm currently running) after I noticed that my BIOS, GRUB, and the Ubuntu boot screen don't have this bar, but the live boot off my usb did! I went through the settings of my monitor and reset it, restarted my PC a few dozen times, unplugged and plugged back in, yadda yadda yadda, normal troubleshooting stuff.

Any ideas? Thanks!

---

### Post by HermanAB on 2019-02-28
The screen, keyboard and mouse are handled by Xorg.  At startup, the system loads a simple generic video driver which works with anything.  At login, Xorg talks to the screen over a serial connection of the VGA or HDMI port to find out what it is capable of and then loads the correct driver and set the resolution.  If there is something wrong with the screen cable/port or if a bad driver is loaded, the screen will not work right anymore, even though it may have worked right just a moment before.  

Since UNIX is a very reliable system, rebooting and turning on/off will usually just bring you back to exactly the same situation. This is all of course rather befuddling to the uninitiated.

You can change things after the fact with a utility called xrandr:
[https://www.x.org/releases/X11R7.5/doc/man/man1/xrandr.1.html](https://www.x.org/releases/X11R7.5/doc/man/man1/xrandr.1.html)

---

