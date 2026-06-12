---
title: "gnome wont load properly"
date: 2007-12-24
forum: General Help
---

### Post by .Michael on 2007-12-24
It all started with me wanting to have 3d desktop effects.
I try to revert my video driver to the way it was when i installed it. This made it slow as hell.
I install the xserver-xgl package. 3d desktop still wont work.
I keep trying to get it to load but it wont load.
its still very slow as if i was on an 8086 =-O

---

### Post by ~LoKe on 2007-12-24
Gutsy comes with 3d effects enabled by default, you just have to enable them.

Are you running Gutsy?  If not, you probably should be.

Remove xserver-xgl:
> sudo dpkg -r xserver-xgl
Then in a terminal type:
> sudo dpkg-reconfigure -phigh xserver-xorg
And ctrl+alt+backspace to restart the xserver, and all should be well.

---

### Post by .Michael on 2007-12-24
now gnome is working..

but why cant i enable desktop effects anymore?
at 1st I was able to then i tried to update the driver.
Now it stopped working, with no way to revert it back.
I have an intel 945 gm graphics board

---

