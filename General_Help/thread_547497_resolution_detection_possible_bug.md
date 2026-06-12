---
title: "resolution detection possible bug"
date: 2007-09-10
forum: General Help
---

### Post by yaywoop on 2007-09-10
I am running xubuntu 7.04 with a nvidia graphics card. 
all was running fine, my screen resolution was detected at install and set at 1280×1024.
then today i turned on the computer without the monitor plugged in. i later plugged in the monitor after  x had started and the resolution was 800x600.
after a reboot with the monitor plugged in it was still at 800x600

"Applications > settings > display settings" only displays resolutions up to 800x600. before it displayed a lot more

I am guessing that when x starts up it senses the monitor connected and adjusts the resolution. because it found no monitor it defaulted to 800x600? and now it is stuck.

any help would be appreciated

---

### Post by coggins on 2007-09-10
You could try editing your /etc/X11/xorg.conf  

Please make a copy of the old xorg.conf before making any changes!  

You'll need to edit as root user.

Find  Section "Screen" 
If there are several, then look for the one you use.  I guess that should be called "Default Screen" but YMMV.
Note the Defaultdepth value
Just further down the file there will be a bunch of SubSection "Display" for each possible Depth.  In the one that corresponds to the Defaultdepth value, check that the first value after Modes is your desired resolution.

save.

CTRL-ALT-BACKSPACE to restart X (fingers crossed)

The resolution should have changed.  If it hasn't, or if it changed but not the way you expected, try changing it with the normal GUI methods - hopefully you will now see the option you wanted in the first place.  For some reason you sometimes have to change the setting in two places before it works exactly right.

---

### Post by yaywoop on 2007-09-11
this is an extract from my xorg.conf file (I haven't changed anything)

> Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"P95f+-2"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"2048x1536"	"1920x1440"	"1792x1344"	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"2048x1536"	"1920x1440"	"1792x1344"	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"2048x1536"	"1920x1440"	"1792x1344"	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"2048x1536"	"1920x1440"	"1792x1344"	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"2048x1536"	"1920x1440"	"1792x1344"	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"2048x1536"	"1920x1440"	"1792x1344"	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

so the default depth is 24, if the first mode in depth 24 is "2048x1536" shouldn't all be fine?

---

### Post by coggins on 2007-09-11
Yeah that looks to be in order...  
It may still be worth trying the resolution you know worked before as the first one in the list.  As I say, I've had several experiences where just changing an entry in that section to a sensible value was enough.  I hate recommending a course of action that makes no sense though...

Also, earlier in your xorg.conf there should be a Section "Device" that corresponds to name of your device as shown under Section "Screen".  You might check that the info there makes sense, particularly the driver, which should be nvidia I guess.

Or maybe the option to use restricted drivers (GUI) has been inadvertently turned off?  Just thinking out loud..

Unfortunately my knowledge of this stuff is limited to fixing things I've broken before, so I'm out of ideas.

Anyone else?

---

### Post by yaywoop on 2007-09-12
i installed the restricted (legacy) nvidia driver. it did nothing to help my situation and i don't think it has a separate configuration utility.
how does ubuntu handle the configuration of X. does it do it through xorg.conf? i mean when you use the gui tools to change settings.

this is the section before what i posted last time
> Section "Device"
	Identifier	"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"NoLogo"	"True"
	Option		"AllowGLXWithComposite"	"True"
EndSection

Section "Monitor"
	Identifier	"P95f+-2"
	Option		"DPMS"
EndSection


---

### Post by yaywoop on 2007-09-12
> **coggins said:**
> Yeah that looks to be in order...  
It may still be worth trying the resolution you know worked before as the first one in the list.  As I say, I've had several experiences where just changing an entry in that section to a sensible value was enough.  I hate recommending a course of action that makes no sense though...


this didn't work
thanks for your suggestions anyway.
its little bugs like this that really annoy me about linux distro's

---

### Post by splintercellguy on 2007-09-12
Backup your /etc/X11/xorg.conf by doing:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

and run:

sudo dpkg-reconfigure xserver-xorg

to reconfigure xorg.conf.

---

### Post by yaywoop on 2007-09-12
HOORAY! thanks splintercellguy.
that fixed it up
so is this a bug or what?
all i did was not have the screen plugged in and the config got screwed

damn. now my scroll wheel doesn't work...

---

### Post by yaywoop on 2007-09-12
i got the mouse working using the imps2 interface

---

