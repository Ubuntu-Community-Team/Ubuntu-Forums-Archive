---
title: "Fresh installation hardy 8.04 - without 3d effects"
date: 2008-06-09
forum: General Help
---

### Post by 3xistence on 2008-06-09
hi to everybody, 
i recently switched from gutsy to hardy but now 3d effects doesn't work. 
It's strange because they usually works with gutsy gibbon O_o
i'm using a laptop with ati mobility radeon 9700
here's some tag

> lspci
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]


> glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX/SSE2 TCL


> glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project


> xorg.conf (only video references)
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Hope you can help me and everybodies with the same problem

---

### Post by Forlong on 2008-06-09
Try this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by 3xistence on 2008-06-10
sorry if i usen't your script before,
i watched the link 
> [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/152271](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/152271)
so i thinked it was a blacklisted Ati card, mine.
but as you say on your webpage i can't understand what's the problem, i never used xgl and i never used ati official linux driver and compiz always worked before on gutsy.
Whit Mesa open driver always worked well compiz (with not a very high frame rate, but man...it works well) and now i don't understand why with hardy (technically advanced than gutsy) it doesn't work.
What happened ?!?

> **Forlong said:**
> Try this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

i need just to run the script and quote here the result?

---

### Post by Forlong on 2008-06-10
If you run the script, it should offer to fix the issue for you.

If not, post the results here.

---

### Post by 3xistence on 2008-06-11
Thanks a lot Forlong, yesterday i downloaded compiz-check but without success, i will try to download it now and i will run it tonight.
tomorrow i will tell you what happend.

just a question because I'm curious, what kind of video card do you have?

---

### Post by Forlong on 2008-06-11
Me? A Radeon 9600XT (have a look at the thread I linked, Compiz-Check tells you that -- well... except for the XT ;))

---

### Post by 3xistence on 2008-06-11
yep, i saw it :)
and you managed to run compiz with your card?

aaah, i just don't saw the "chmod etc..." ... sorry ;P
I used to open it as a .rar archive

---

### Post by Forlong on 2008-06-11
> **3xistence said:**
> yep, i saw it :)
and you managed to run compiz with your card?
Yep, running Beryl/Compiz since Edgy (Ubuntu 6.10) pretty successfully.

ATI's Linux support still sucks, though.

---

### Post by 3xistence on 2008-06-11
> **Forlong said:**
> Yep, running Beryl/Compiz since Edgy (Ubuntu 6.10) pretty successfully.

ATI's Linux support still sucks, though.

True, ATI's linux support sucks.
Since edgy :shock:

i'm new with Ubuntu, i never tried Edgy, i just started with Gutsy and Compiz works well also with Open driver (just some problem with  few screensavers).
Now i will try to fix hardy (probably mine's a blacklisted card on laptop).

Nice new avatar "blender" ;)
thanks again for your support

---

### Post by 3xistence on 2008-06-12
Now works! my ati on laptop was blacklisted and with your script i managed to skip the checks in order to run compiz.

Thanks a lot Forlong, your script need to be built-in with the next distro of ubuntu!

thanks a lot again, without you i wasn't able to fix it

---

