---
title: "Why is my Radeon 9800 acting like a 9500?"
date: 2007-02-06
forum: General Help
---

### Post by aldenhg on 2007-02-06
I'm running Edgy with AIGLX and Beryl on a 9800 Pro with the OSS radeon driver. I've been having issues with anything that requires pixel shaders; namely they won't work. I get render errors to the tune of GL_ARB_fragment_program is missing. That's not my main issue (though I would love any insight into it) - when I was trying to figue out what the deal was I ran glxinfo and came across a line that said 
> 
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1

"What's the problem?" you may be asking. Well, the problem is that the 9800 Pro has the R350 chip and runs at AGP 8x. I can't for the life of me figure out how to fix it. Here's the Device section of my xorg.conf file for reference:
> 
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver		"radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	BusID		"PCI:1:0:0"
EndSection

The reason AGPMode and AGPFastWrite are commented out is because if they aren't X won't start.
Also, I may be misunderstanding what the AGPSize option does, but my 9800 has 128Mb of RAM.
In case it's not obvious, I want my card running at it's full spec. Any help would be greatly appreciated.
Alden

---

### Post by stueyboy on 2007-02-07
Hi there. Here is the GPU section from my xorg.conf file. Maybe try some of thesettings in there.

> Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver		"radeon"
	Option		"AGPFastWrite" "yes"
	Option		"AGPMode" "8"
	Option		"ColorTiling" "on"
	Option		"EnablePageFlip" "true"
	Option		"AccelMethod" "EXA"
	Option		"XAANoOffScreenPixMaps"
	Option		"RenderAccel" "true"
	Option		"DRI" "true"
	BusID		"PCI:1:0:0"
EndSection

EDIT - Just read the end of your post and I had that problem the first time I installed ubuntu but the next time, it worked fine and I could get the AGP mode up to x8. I also thought that you should make the AGP aperture size to twice the RAM on the board but I do that in the BIOS anyway.

---

### Post by aldenhg on 2007-02-07
Well, I was able to get it running at 8x, but if I put the AGP aperture to anything higher than 64 X crashes when I try and run anything 3d (beryl, glxgears). Also, if I try and turn on AGPFastWrite X simply won't start and the whole system goes into a hard lock.
Call it overconfidence, but I'm pretty sure that if I can force the Mesa drivers to treat my card like the R350 it is instead of the R300 it isn't everything will work just dandy. The only issue is that I have no idea how to do that.

EDIT:
stueyboy, is there any chance you could do me a favor and post the output you get when you run "glxinfo | grep OpenGL"?

---

### Post by aldenhg on 2007-02-09
Never mind this thread. After some more research I learned that the R300 Mesa driver supports the R350 chips. The only issue is that the drivers don't have a GL_ARB_fragment program, which explains why I can't get everything in Beryl to work properly. I guess i'll be waiting for a driver update.

---

