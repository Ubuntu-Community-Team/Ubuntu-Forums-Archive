---
title: "Xorg chews through my CPU"
date: 2007-11-11
forum: General Help
---

### Post by bobbarker on 2007-11-11
Xorg is eating up my CPU whenever I use firefox. Usually my CPU sits happy at 600mhz while I browse but lately it's been sticking at the full 1.6ghz. It's not "heavy" web pages doing this, it's locked up on basic HTML pages and web 2.0 pages alike. With firefox in the background, even scrolling man pages takes a hit.

The only two recent changes to my system is I switched up the driver for my computer, it's now the "radeon" driver (open source one, I believe), but that showed an improvement in performance. There is also a little shell script from ThinkWiki for controlling my fans, but disabling that doesn't do anything (only kills my fans).
I've also started tinkering with video card overclocking (wine + CS + old laptop requires it), but I only overclock it when I'm actually gaming, rest of the time it's back to normal.

System Specs:
Thinkpad X31
1.6ghz Centrino
768MB RAM
ATi Radeon M6 (16MB)

This is a snippet of my xorg.conf, minus stuff involving touchpads & other stuff.
```

Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility M6 LY"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on"
	Option		"SWcursor" "off"
	Option		"EnablePageFlip" "on"
	Option		"AccelMethod" "EXA"
	Option		"DynamicClocks" "off"
	Option		"BIOSHotkeys"   "on"
	Option		"AGPSize" "32"
	Option		"EnableDepthMoves" "true"
EndSection 


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
	Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

I could go back to the default ati driver, but I'd rather not :(

---

### Post by justin_guerin on 2007-11-11
You might reduce the CPU use if you turn off smooth scrolling in FF, if it's on.  You'd probably also cut down if you turned off auto spell check.

If those don't work, you might try tinkering with some of your Xorg options.  You've explicitly set a few options that are not the default for the radeon driver, and while there's no guarantee choosing the default would reduce your CPU use, it's possible.  

However, I would not expect those options to make a big difference if they were set when you were using the ati driver.  Did you change anything else when you switched?

Also, if FF the only application that uses the CPU heavily?  If it is, did it do that when you were using the ati driver?  Sounds like the answers are "yes" and "no", in which case, it may be a driver problem, and the only thing to do is go back or tweak the settings for the radeon driver until you're happy with performance.

Good luck,
Justin

---

### Post by eldragon on 2007-11-11
do you have vino up and running?

even if you dont connect to the server, disable it and see if it gets better...

---

### Post by bobbarker on 2007-11-12
I'll tinker with the driver options since those are the only things that have majorly changed...and since they're directly related to xorg. FF is the only app that causes this, but FF itself isn't doing anything, it's just affected by xorg's CPU hogging.

I don't have vino running but I'll try that.

---

### Post by NT4usB on 2007-11-12
Flash stuff on pages makes Firefox use cycles. Do you have (the latest?) flash installed?
Might try the flashblock plugin... see if that helps.
[https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)

ed: did some googling and there's several bugs related to images and the way Firefox handles compressed and uncompressed images. 
Might try addblock along with flashblock. I inatall both before I ever go surfing so I don't know how Firefox behaves without them.
also things like addons, themes. Animated cursors...

---

### Post by bobbarker on 2007-11-14
I ran a quick
sudo dpkg-reconfigure xserver-xorg
and reset to the standard 'ati' driver and the system runs soooooo much smoother. No stupid little hangs when minimizing stuff and webpage scrolling is smooth again. I'll take another stab at the radeon driver eventually.

EDIT:
My average CPU load went from about 75% down to 15% (normal browsing)....made a biiiig difference.

---

