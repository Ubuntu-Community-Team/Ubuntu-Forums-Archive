---
title: "Installing on TV screen using DVI-to-HDMI"
date: 2007-10-08
forum: General Help
---

### Post by BFP on 2007-10-08
I've recently gotten a spare computer, and I decided to attach it to our HDTV via a DVI-to-HDMI cable to use as a set-top box for playing video, and eventually to make into a fileserver for the house. However, when I hook the system up to the TV (I used Ubuntu 7.04), I can only get the resolution to set to 640 by 480, which stretches off of the screen on all sides. 

What do I need to change to get the resolution up to a normal amount, presumably 1080i?

---

### Post by scapalexis888 on 2007-10-08
System>prefs>screen resolution? And also keep in mind the max resolution your video card can support

---

### Post by BFP on 2007-10-08
The Screen Resolution option only displays 640x480. My video card is a GeForce FX5500- on a normal monitor, it can do 1280x1024 quite easily, so it ought to be able to do at least that on this TV.

---

### Post by rsambuca on 2007-10-08
There are a number of things to consider when connecting a computer to a TV.  

First, what type of tv is it?  If it is DLP or some other type of rear projection, then there will be overscan.

Two, what resolutions does your tv accept?

What is your xorg.conf look like?

---

### Post by BFP on 2007-10-08
The TV is a Samsung SlimFit CRT. It accepts 720p and 1080i.

The relevant sections of xorg.conf (I think) are: 

> Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5500]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5500]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection


I orginally installed on a normal monitor before moving the computer over to the TV. Would I get better results if I reinstalled Ubuntu using this monitor and setup?

---

### Post by rsambuca on 2007-10-08
You shouldn't have to re-install just for this.  You'll just have to re-configure your xorg for the different settings required by your tv.  Personally I would install the nvidia proprietary drivers if you aren't philosophically opposed to such things.

---

### Post by BFP on 2007-10-08
I don't object to installing proprietary drivers, or to editing the xorg.conf file, but I'm not certain of exactly which changes I should make. Also, what's the best way to install the proprietary drivers- I've made some attempts at this before but usually ended up just breaking X.

---

### Post by BFP on 2007-10-08
Okay, the Restricted Drivers Manager was able to install the proprietary nvidia drivers. Having these gave me two choices of resolution instead of one, so I'm now displaying at 800x600. I still think the TV should be able to go to something like 1300x768. What kind of edits does the xorg.conf need in order to make this work?

Also, is there anything that can be done to offset the overscan so that I can see my menu bar and properly fullscreen video?

---

### Post by rsambuca on 2007-10-08
I would try the Restricted Drivers Manager first.

EDIT.  Oh, you found it yourself!

---

### Post by Naoi on 2007-10-11
These links give some advice on setting up TV out with nvidia 

From nvidia readme :
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/chapter-16.html]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/chapter-16.html")

A howto from these forums:
[http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)

I have gotten tv out to work with 720p using component input to my HDTV, but 1080i just gives me a blank screen. (I haven't tried my DVI input because I use that for my DVD player.)

I haven't been able to remove overscan either unless I switch to the VGA (RGB) input on my TV and program a special modeline which was a lot of trial and error.

I can get 1080i (and 720p), and I was able to customize the component resolution in Windows so I guess it's a linux driver issue.

Good luck :)

---

