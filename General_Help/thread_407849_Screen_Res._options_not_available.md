---
title: "Screen Res. options not available"
date: 2007-04-12
forum: General Help
---

### Post by chucktx on 2007-04-12
Every video card I have tried with the Live CD the highest screen resolution I get is 800x600.  I have installed Ubuntu 6.10 w/ a Voodoo3 3000 and the screen reolution is still the same options 640x480 & 800x600.  When I installed SUSE on the same hardware 1024x768 was available & did work.  Every time I have run the x reconfiguration I always break X & get no screen errors.

Any suggestions on how to get higher than 800x600 on my voodoo card with 6.10?

Thanks, Chuck

---

### Post by PetePete on 2007-04-13
do you have the correct drivers installed for the gfx card?

try editing the /etc/X11/xorg.conf and manually specify the resolutions to use. ....i'm at work currently (no linux :( ) but i think its about half way down taht file, anyway you will know what i mean as its the bit which has lots of resolutions ... 

if you get stuck serach for xorg.conf resolutions and you should find something helpful.

---

### Post by chucktx on 2007-04-13
The voodoo3 3000 is a 16bit depth video card.  In /etc/X11/xorg.conf all of the bit depths have 1024x768 as the highest available resolution.  This option is not available however in the "screen resolution" properties app in the preferences menu.  I do not know how to force it to use something in the xorg.conf file.

Thanks, Chuck

---

### Post by chucktx on 2007-04-27
This problem was solved.  Here is a link to the thread where the resolution is. [http://ubuntuforums.org/showthread.php?t=407911]("http://ubuntuforums.org/showthread.php?t=407911")

I still don't know of a way to fix this w/o modifying files manually.

---

