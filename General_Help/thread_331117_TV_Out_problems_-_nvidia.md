---
title: "TV Out problems - nvidia"
date: 2007-01-04
forum: General Help
---

### Post by yezzer on 2007-01-04
Hey board,

i've been googling, and reading threads on these boards, but i'm kinda lost at the moment, as i'm new to all this.

as mentioned in [this thread]("http://www.ubuntuforums.org/showthread.php?p=1965839#post1965839"), i've looked at the [HOWTO: Nvidia easy TV out]("http://doc.gwos.org/index.php/Nvidia_easy_tv_out") - i had to chmod 777 /usr/local/bin/tv-on and /usr/local/bin/tv-off (is 777 right? at least it works..)

So - anyway - it's not outputting to TV. When ubuntu boots and shuts down it outputs to TV, but I cant get it working any other way.. i've tried playing with the NVTV GUI, to no avail... i'm using a PAL TV btw..

any ideas anyone? Or are there forums this would be better posted in?

Cheers!

---

### Post by yezzer on 2007-01-04
oh yeah - i'm using SVIDEO out, and my card is a geforce 5600 [Leadtek winfast A310]("http://www.leadtek.com/3d_graphic/winfast_a310_td_myvivo_1.html")

---

### Post by pseudonym on 2007-01-04
Hi, here are some tips which may help you -

1. Not all nvidia cards are supported by nvtv. If your card is a relatively new one, it's almost certain that it isn't supported. I bought a 6600 GT (not that new a card now) about a year ago and nvtv wouldn't work with it. And according to the [nvtv project page]("http://sourceforge.net/forum/forum.php?forum_id=105850") it's *still* not supported. So it's safe to assume thate every card made since that is not supported, either, and possibly even several of the FX 5000 series, too.

2. nvtv will *not* work with the open-source 'nv' driver. You *must* have installed the 'nvidia' driver for it to work at all.

3. If nvtv does not work with your card, you need to use the [standard method]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/appendix-h.html") of TV-out configuration from the nvidia readme. You should read that section plus [this one]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/appendix-p.html") about multiple X screens to understand it fully.

4. The instructions in step 3 should be enough, but here are the relevant sections from my xorg.conf which you can use as a reference - ```
Section "Device"
	Identifier	"NV GF 7950 GT"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
    Screen      0
    Option      "UseDisplayDevice"  "DFP"
    Option      "DPMS"   "true"
    Option      "NoLogo"  "1"
EndSection

Section "Device"
	Identifier	"S-VIDEO"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
    Screen      1
    Option      "TVStandard"  "PAL-B"
    Option      "TVOutFormat"  "SVIDEO"
    Option      "UseDisplayDevice"  "TV"
    Option      "TVOverScan"  "0.9"
    Option      "DPMS"  "true"
    Option      "NoLogo"  "1"
EndSection

Section "Monitor"
	Identifier	"DFP-0"
	Option		"DPMS"
	HorizSync	31-60
	VertRefresh	56-75
EndSection

Section "Monitor"
	Identifier	"TV-0"
	Option		"DPMS"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"NV GF 7950 GT"
	Monitor		"DFP-0"
	DefaultDepth	24
	SubSection "Display"
        ViewPort    0 0
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
    SubSection "Display"
        ViewPort    0 0
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
        ViewPort    0 0
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
        ViewPort    0 0
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"S-VIDEO"
	Monitor		"TV-0"
	DefaultDepth	24
	SubSection "Display"
        ViewPort    0 0
		Depth		8
		Modes		"800x600"
	EndSubSection
    SubSection "Display"
        ViewPort    0 0
		Depth		15
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
        ViewPort    0 0
		Depth		16
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
        ViewPort    0 0
		Depth		24
		Modes		"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Screen0"
    Screen		1 "Screen1" RightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Mouse0"
    Option      "OffTime" "10"
EndSection

```
5. Don't mean to lecture you, but if you don't already know, you should insert links in your post using the world/chain symbol on the toolbar. Just paste in the link in the popup box and in between the tags write how you want it to appear in your post. Your post will be neater and easier to read this way.

HTh :)

EDIT - Your second post appeared as I was typing this up. :)

---

