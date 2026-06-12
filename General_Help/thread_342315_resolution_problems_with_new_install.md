---
title: "resolution problems with new install"
date: 2007-01-19
forum: General Help
---

### Post by eXidos on 2007-01-19
I just got a new HDD and installed a fresh copy of ubuntu 6.10 but I cant seem to get the resolution to change it is maxed out at 640*480 even thought my xorg.conf is set to depth 24 and max on 24 is 1600*1200.

so i deleted everything other than 1600*1200 in depth 24 but still no change. I have installed the latest Nvidia drivers (not the beta) and it is running the proper driver for my monitor but i dont know whats wrong; any thoughts?

Note - I was having problems installing to this drive I tried many times to get Ubuntu 7.04 up and running but failed each time during the hardware install. Dont think this matter but I'll try anything

---

### Post by Kateikyoushi on 2007-01-19
What is your video card are you sure it has enough ram to display that resolution in 24bit ?
In your xorg.conf is the driver set to nvidia ?

---

### Post by Dave54 on 2007-01-19
You should find out whether you're stuck at 640x480 or if your monitor just can't display 1600x1200x24@the refresh you're trying to use. Try for 800x600x a lower bitrate @ like 60 Hz

---

### Post by eXidos on 2007-01-19
I have a geforce 4 mx 440 w/64mb ram and a viewsonic 19in this configuration has worked at 1600*1200 for quite a while but i'll try a lower setting. and yes it is set to nvidia

---

### Post by Kateikyoushi on 2007-01-19
That should do it. Did you try to recnfigure X ?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by eXidos on 2007-01-20
ok i reconfigured x set default res to 1280*1024 and color to 24 still no go my "screen resolution" setting in prefrences only show 640*480

---

### Post by Kateikyoushi on 2007-01-20
Then check TSeliot's Nvidia guide. Here's a link to the problems section. [LINK]("http://www.albertomilone.com/latest_nvidia_udsf_edgy.html#PROBLEMS_SECTION")

---

### Post by eXidos on 2007-01-20
I was going through the logs for xorg start up and found this:

(--) NVIDIA(0): Connected display device(s) on GeForce4 MX 440 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option



**This is my xorg.conf the stuff that matters anyway:**

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection


Section "Device"
	Identifier	"Nvidia Geforce nv11 mx 440"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	64000
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia Geforce nv11 mx 440"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by eXidos on 2007-01-20
when I set the driver back to nv insted of nvidia it allowed me to go to 800*600

---

### Post by eXidos on 2007-01-20
I went throught TSeliot's Nvidia guide for install and the special geforce mx440 section but nothin the xorg log still showed the same error as i posted before.

---

### Post by eXidos on 2007-01-21
I'm going to try and reinstall and maybe a new monitor dont know why it wont work now but hopefully this will fix it

---

### Post by eXidos on 2007-01-21
ok the problem is most defenatly the monitor I changed to my 17in and it allowed me to go to 1280x1024 with no driver or video card change and i did not even have to reinstall! then I chaned to monitors while the computer was still on and running in 1280*1024 and it ran fine on the 19in...little scared to reboot though, ill do my best not to!

---

### Post by Michael Teofilov on 2007-01-21
I would suggest you the X.Org web page ([www.x.org)](www.x.org)), once there go to the Wiki section and type in your search (or just the model of your video card). That worked for me with a problem that had me stuck for almost a week. They have a nice test performed on your system (you should alow it) and then give you a list of possible solutions.

---

