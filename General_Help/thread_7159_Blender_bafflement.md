---
title: "Blender bafflement"
date: 2004-12-04
forum: General Help
---

### Post by franx on 2004-12-04
I've been unable to launch either Blender 2.33 or the upgraded Blender 2.34 installed from the universe repository.  Here's the readout I get:

franx@ubuntu:~ $ blender
/usr/bin/blender: line 35: 30541 Segmentation fault      blender-bin $@
franx@ubuntu:~ $

I'm running an iMac G3/350 with 256 megs of RAM and a built-in ATI Rage RL card with 8 megs of VRAM.  DRI/3D acceleration is working fine on other programs.

Any ideas how to make this work?

TIA,
franx

---

### Post by wiseNoob on 2004-12-04
not sure about you particular setup.  when I tried the OSX version on my ibook 2.2, same vid card, it crapped out on me more often than not, but that was quite a few versions ago.

heres what I did (keep in mind, I am on an x86 w/ 128mb nvidia GeForce 4200 Ti):

I dl'd and unpacked blender 2.35b from blender3d.org

[http://www.blender3d.org/cms/Blender.31.0.html](http://www.blender3d.org/cms/Blender.31.0.html) - use the static version if you have a lesser video card.

unpack in your home directory in a folder of your choosing, and drag the "blender" file  to the gnome panel (sorry, the only way I know how) - a dialog will pop up: name it blender, choose an icon, and in the "command" field, go to the end of the line and type <space> -w for opening in a managable window and type nothing to open it full screen.

This does cause an inert bug: see here for details...
[http://www.blender3d.org/cms/Linux.301.0.html#1950](http://www.blender3d.org/cms/Linux.301.0.html#1950)

still have no idea what directory .Blanguages is in, but it seems to be an issuethat can be ignored.

---

