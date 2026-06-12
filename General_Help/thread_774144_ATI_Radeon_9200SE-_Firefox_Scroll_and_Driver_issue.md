---
title: "ATI Radeon 9200SE- Firefox Scroll and Driver issue"
date: 2008-04-29
forum: General Help
---

### Post by The_Seeker on 2008-04-29
Hello everyone ,

I'm a new member to the Ubuntu (and Linux) user community. I recently installed Hardy Heron on my computer. The following are the hardware specs:

P4 2.6 Ghz
512 MB RAM
** ATI Radeon 9200 SE - 128 MB **

Everything works perfectly fine, but I am running into a couple of issues:-

1) ** Scrolling in Firefox is very jerky/choppy:** I found that if i set Visual Effects to *None*, this problem is solved but this results in no eye-candy :(

2) ** No desktop cube ** : If i do set my Visual effects to *Extra*, I dont see many of the features that come along with Compiz.

I ran the following commands in the terminal:

```
 glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

```

**Xorg.conf file**

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

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
EndSection

```

Is there any way i can get the best of both worlds (i.e. (1) and (2) )? I think there is a driver issue as I cannot see anything in the xorg.conf file. 

Any help in this regard will be much appreciated. Awaiting your responses.

Thanks in advance :)

---

### Post by JonnyB29 on 2008-05-02
hi

i have exactly them same problem in 2 pcs with ati 9200
waiting for a solution

bye

---

### Post by fahimdadream on 2008-05-02
Hey, 

Im not sure about the choppy FireFox scrolling, since I'm having the same problem on my nvidia graphics card. However, the problem with seeing all the effects, have you tried installing the advanced configuration options for compiz to be able to edit all the effects? Try searching the forums or google for that. Also, you can download the compiz fusion icon from "Add/Remove.." and that should give you the same options. Hope this helps, and good luck.

---

### Post by gatos on 2008-05-04
Hi
I am new to Linux, having started with Ubuntu Gutsy 7.10 3 months ago. I had hardly any issues with Gutsy and I got Compiz fusion running with no issues. I did a new install of Hardy Heron and had exactly the same problem you did. I am using ATI Radeon mobility 9200 and could not get the cube etc to work at all. In actual fact I could not turn any of the visual effects let alone the advanced effects. I searched online for quite a few days but no solution yet. I tried everything with my computer settings but no solution either. I tried the ATI proprietary drivers and guess what, no luck. I have since gone back to Gutsy  and setup all the advance visual effects with no problems. I will keep an eye and if a solution comes up, I will let you know. Good luck everyone

---

