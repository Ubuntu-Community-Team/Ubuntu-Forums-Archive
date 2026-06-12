---
title: "Xorg update killed open GL"
date: 2007-01-10
forum: General Help
---

### Post by GQed76 on 2007-01-10
After todays update I can not use Open GL. It seems its "Missing".  Any ideas where to start?

---

### Post by gunthr on 2007-01-10
I got hit worse by the update. It kill X all together. I can't boot into Gnome. It just keeps looping back to the Grub login screen. Does anyone know if there is a way to reverse the changes the updates made?

---

### Post by NT4usB on 2007-01-10
I saw the update but put it off until I have time to recompile my video driver, lirc, etc... Getting used to these third party things breaking with kernel upgrades.

---

### Post by Delkster on 2007-01-10
> **GQed76 said:**
> After todays update I can not use Open GL. It seems its "Missing".  Any ideas where to start?

Have you installed your OpenGL drivers from a third party rather than from Ubuntu's repositories? If you have, you probably have to reinstall the driver, or remove it and go back to the Ubuntu-provided drivers (those shouldn't break on kernel updates as the external driver modules are also updated accordingly, but for 3rd party drivers that doesn't happen automatically).

---

### Post by currentshades on 2007-01-10
I have the same problem as gunthr!  I'm getting this error.
"I've detected another panel running and will now exit."

---

### Post by ~LoKe on 2007-01-10
> **gunthr said:**
> I got hit worse by the update. It kill X all together. I can't boot into Gnome. It just keeps looping back to the Grub login screen. Does anyone know if there is a way to reverse the changes the updates made?

Just run the package to reinstall the drivers.  "sudo sh NV*.run"

---

### Post by gunthr on 2007-01-10
Sorry, I should have been more specific. I have an ATI card, not NVidia. I am going to try to figure out how I installed it before and try that again. Thanks for you help.

---

### Post by gunthr on 2007-01-10
Lame, it didn't work. I reinstall the fglrx driver as I originally did and have the same problem. Another thing I noticed is that df says my / partition is at 100%. It isn't, but is pretty close, so I moved some files and now there should be about 1.5GB free. df still says 100%. du -sh / says it's 25G, which is wierd since it's partitioned to 15GB. Think this is related or just some other lame issue that I need to figure out?

---

### Post by gunthr on 2007-01-10
I did a alt-del-f1 to get to the command line. I then tried to startx. I get the error "cannot create temp file for here document: No space left on device". I guess the root of my problem lies with the disk usage being reported incorrectly. I'll look around the forum, but anyone have any ideas? Thanks!

---

