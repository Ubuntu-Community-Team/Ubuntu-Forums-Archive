---
title: "PATCHING with a .patch file...HOW?! Getting Thinkpad Ultranav to work"
date: 2006-11-04
forum: General Help
---

### Post by shinikaru on 2006-11-04
Okay, I have a thinkpad with an ultranav. It's a little button to hold down and then moving the mouse up an down scrolls. I've decided to finally move to linux but this button is something I regularly use and it does not work in dapper. 

[http://www.thinkwiki.org/wiki/Patch_to_enable_advanced_trackpoint_configuration](http://www.thinkwiki.org/wiki/Patch_to_enable_advanced_trackpoint_configuration)
I've done every single damned thing, I've tried to install XFree86 and use the "make" command in the terminal to make the driver and then put it in the correct folder, but, even after I tried to install that, "make" is still not a valid command.
Hours later I give up that, another way is this .patch file.

What the hell do I do with it?
I tried going in the terminal
patch -i synaptics-scroll-wheel-2.6.11-rc1.patch
then it goes through OK, and asks, "File to patch: "
...How the hell am I supposed to know that?

Please help me, I'm as frustrated as any linux newbie could be.

---

### Post by pay on 2006-11-04
It says on the site "since 2.6.14-rc5 the patch is included in the mainline kernel" and Ubuntu 6.06 and 6.10 use newer kernels than that one (uname -r). So patching it shouldn't be necessary. To compile programs you need gcc, to install it type ```
sudo aptitude install build-essential
``` into the terminal.

---

### Post by shinikaru on 2006-11-04
Thanks, that was certainly simple. Now I've "make" works

> 
2. Copy the driver module "synaptics_drv.o" into the XFree module
   path. This path is usually "/usr/X11R6/lib/modules/input/", and
   running "make install" as root will do this for you. Note though
   that some distributions have a different module path. For example,
   in Gentoo 1.4 (with XFree86 4.3.0), the correct path is
   "/usr/X11R6/lib/modules/drivers".

Okay, so I did "make install" and that apparently went well.
Now...> 
3. Add the driver to the XFree configuration file (usually called
   /etc/X11/XF86Config-4 or /etc/X11/XF86Config)

/etc/X11/XF86Config does not exist. Wtf?

---

### Post by pay on 2006-11-04
I think that xorg replaces xfree86, but I may be wrong so don't quote me.

---

### Post by shinikaru on 2006-11-04
that makes sense, i've made the requested changes in xorg config instead.

I don't know how to "restart the x server"
as restartx or stopx don't work and startx requires it to be stopped first..

I'm just going to restart completely.

---

### Post by shinikaru on 2006-11-04
Fantastic this still doesn't work T_T

---

### Post by shinikaru on 2006-11-04
How silly... well, after ******* with so much for so many hours, I finally screwed something up in xorg.config.

Meaning... system would not load with a gui. 

I reformatted anyways and the first two things I've done are use THIS REALLY SIMPLE AND EASY FIX FOR THIS:

change xorg.config accordingly
> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option 		"EmulateWheel" 		"on"
	Option 		"EmulateWheelButton" 	"2"
	Option		"YAxisMapping"		"4 5"
	Option		"ZAxisMapping"		"4 5"
EndSection

And the second thing I did was use the ultranav scroller down to this quick reply box ^_^

Edit: Actually, this doesn't work correctly.
	Option		"XAxisMapping"		"6 7"

Scrolling up/down works well, but if I move the mouse left/right then I start going Forward/Backward in pages.
Any way to disable horizontle scroll?
I just tried disabling Emulate3Buttons but that didn't work.


final edit:

Flawless! Turned X Acis Mapping off.

almost there! little help

---

