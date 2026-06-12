---
title: "Gutsy video problems`"
date: 2007-10-18
forum: General Help
---

### Post by feest on 2007-10-18
Let me first say i'm very dissapointed in gutsy... The nvidia drivers don't seem to work at all on my machine and the dual screen configuration doesn't work either... The xrandr extension also doesn't work and finnally the wallpaper is ugly...

But my problems is that I'm not able to configure my pc to a workable configuration... Every boot my system gets stuck in low graphics mode and everytime i configure dual screen (and it actually works, change 1/100) the right screen has a 1:1 ratio in stead of 4:3 but still running it's native resolution of 1024*768. None of the utilities to configure X seem to work and the drivers just suck. How can this happen to Ubuntu and how can this be fixed?

---

### Post by Light- on 2007-10-18
I am having the exact same problem (except my card is ATI), can someone please help?

---

### Post by 11touche on 2007-10-19
Same thing here. Is it a dual-head only problem?
Stuck under low graphics mode, and everytime I reboot, it switch back to Vesa driver (800x600)

---

### Post by Agent86 on 2007-10-19
I am having a similar problem. It keeps booting into low-res, even after I configure it to use my LCD and my Nvidia card. I even tried to copy over my /etc/X11/xorg.conf file that I had backed up before the upgrade, and it STILL boots into low-res mode. And I am NOT running dual-head, so that's not the problem.

I am running Xubuntu, and I upgraded using the alternate CD. When I go into Display settings, the only res choices I am given are Default of 800x600, and 640x480. The changes I make using the xorg configure tool during boot don't seem to have any effect.

---

### Post by waltervalderrama on 2007-10-20
Hey I have the same problem. I tried this.
- When PC boots with kernel 2.6.22-14-generic, everything works great.
- But when PC boots with 2.6.22-14-i386 Gutsy doenst recognize nvidia drivers and works in 800x600.

I have the following problems too:
- I cannot open "Restricted Drivers" utility, i don't know if the application is missing.
- I cannot open "update-manager" too. When I type the command I get the following: 

andre1@valderrama:~$ update-manager 
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

I don't know if this is related to graphics, I think so.

---

### Post by Agent86 on 2007-10-20
I took care of the problem by disabling the restricted driver, restarting the computer, then doing a Synaptic update and re-enabling the restricted driver.

This thread seems to have more info on the problem:
[http://ubuntuforums.org/showthread.php?t=581119](http://ubuntuforums.org/showthread.php?t=581119)

Walter, you might try asking about your problem in that thread.

---

