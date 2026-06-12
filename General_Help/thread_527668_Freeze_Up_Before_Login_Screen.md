---
title: "Freeze Up Before Login Screen"
date: 2007-08-16
forum: General Help
---

### Post by RTFishUL on 2007-08-16
Ok, strange issue... or maybe not, but I haven't seen anything else that's helpful around.

I rebooted my system today (after installing some updates, stupidly didn't check which ones) and everything goes fine for a while. Boot screen comes up, does that whole deal.

Then, the Nvidia logo shows up as it usually does, but right before it reaches the login screen it dies and I get a grey screen, completely blank.

When this happens, both my mouse and keyboard appear to be off, or not functioning, because I can't do the usual ctrl + alt + 1 to get into the terminal.

I can however boot into recovery mode and start x and everything, use my mouse, keyboard, no problem. Unfortunately, even though I can do that, I don't know what to fix.

I've gotten so frustrated that I just decided to screw it, and do a fresh install of ubuntu (I have my important stuff backed up elsewhere). Just my luck however, the live cd encounters the same freeze up just before the login screen.

Any help/suggestions would be greatly appreciated, even if it means a fresh install without the live cd (which I'm not sure how to do).

---

### Post by merlinus on 2007-08-16
When booted via recovery mode, look at /etc/X11/xorg.conf to see what video driver you are using.

-merlin

---

### Post by RTFishUL on 2007-08-16
Section "Device"
        Identifier      "nVidia Corporation C51G [GeForce 6100]"
        Driver          "nv"
        BusID           "PCI:0:5:0"
EndSection

you mean this?

---

### Post by merlinus on 2007-08-16
Is that info correct (nv driver and bus id}?

Just wondering if something changed with the updates....

You might look at any xorg.conf backups and compare.

-merlin

---

### Post by RTFishUL on 2007-08-16
hmmm, yeah in a lot of them it says the driver is "nvidia" not "nv", the bus id is consistent though... strangely in a few of them it says the device is just "generic video card" and in one the driver is "vesa", wow this is messed up... I'm gonna try changing it to nvidia from nv and reboot, see if that works...

---

### Post by merlinus on 2007-08-16
vesa is the generic catch-all works-with-everything driver, but is not nearly as good as the card-specific one.

It may be that you will need to reinstall the correct driver for your card.

-merlin

---

### Post by RTFishUL on 2007-08-16
ok, so i changed the thinger from nv to nvidia and everything stayed the same on reboot.... except that now instead of a blank grey screen I get one that looks like the nividia logo was smeared everywhere. Gah... I'll try reinstalling the driver... i think that was like... sudo apt-get reinstall nvidia-glx-new or something

---

### Post by RTFishUL on 2007-08-16
nope, nevermind, damn

---

### Post by merlinus on 2007-08-16
You can try using the vesa driver to at least get the gui up-and-running, and then search for a new driver.

-merlin

---

### Post by RTFishUL on 2007-08-16
no good, changing it to vesa gives the same results... still no ability to enter terminal

---

### Post by merlinus on 2007-08-16
Did you check the screen section to make sure it has the same device as in the device section (identifier) and resolutions?

Beyond that, I dunno....

-merlin

---

### Post by RTFishUL on 2007-08-16
That's the screen section... the identifier under Section "Device" was "nVidia Corporation C51G [GeForce 6100]" which as you can see is listed as the device in Section "Screen", not the identifier... although I would think that's how it's supposed to be.

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51G [GeForce 6100]"
	Monitor		"1825"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by merlinus on 2007-08-16
Since xorg.conf seems fine, obviously something else is amiss.

You can continue to try different things, or backup data and reinstall.

I usually find this leads to far less agita now and in the future.

-merlin

---

### Post by RTFishUL on 2007-08-23
Ok, so it isn't a problem with Ubuntu, I know that now.
Just the other day I lost my ability to even boot into recovery mode, and then later, to boot at all.

Since my box is getting power, but not booting, I have a feeling it's something possibly with the motherboard... which would suck. But at least I know it's not Ubuntu now so thanks for the helps.

---

