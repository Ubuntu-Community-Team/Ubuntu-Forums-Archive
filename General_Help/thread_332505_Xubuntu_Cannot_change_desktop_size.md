---
title: "Xubuntu Cannot change desktop size"
date: 2007-01-06
forum: General Help
---

### Post by Frankly3D on 2007-01-06
Hi,

Newbie here.

Installed Xubuntu 6.06.
In display settings, no option to change resolution.
only "default" listed. screen stuck at 640x480 (guess?)

How can I change it? to 800x600 or better

ATI graphics card 128mb Radeon 9600
17" Gateway EV700 monitor.

xorg.conf <SNIP>
Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9600 PRO]"
	Driver		"ati"
	BusID		"PCI:1:3:0"
EndSection

Section "Monitor"
	Identifier	"Gateway ev700"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV280 [Radeon 9600 PRO]"
	Monitor		"Gateway ev700"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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

</snip>

Frank

---

### Post by dermotti on 2007-01-06
Try changing your driver to vesa

Driver "ati" 

to

Driver "Vesa"

Another thing you can try is rebuilding your xorg.conf
make a backup of your current xorg,conf and run

sudo dpkg-reconfigure xserver-xorg

---

### Post by Frankly3D on 2007-01-06
Ok  Thanks for the reply 

sudo dpkg-reconfigure xserver-xorg
and changing to vesa seems to have done it.


Frank

---

### Post by vodsonic on 2007-03-04
I seem to be having a similar problem, which the above solutions won't solve.

I installed Xubuntu on an older PC with a 15" LCD monitor (1024x768 ) . I recently upgraded to a 19" Samsung Syncmaster 931B LCD with a native resolution of 1280x1024. Xubuntu won't switch to use the higher resolution of the new monitor, no matter how sweetly I ask or how loudly I threaten.

Applications > Settings > Display Settings has never shown a resolution higher than 1024x768 in the list, no matter what settings I change.

Here's what I've tried:

1. Adding the native resolution of the new monitor at the beginning of each list of "Modes" that appear in /etc/X11/xorg.conf

2. Re-configuring xorg with "sudo dpkg-reconfigure xserver-xorg"

3. Changing the driver from "ati" to "vesa"

4. Re-running "sudo dpkg-reconfigure xserver-xorg"

After step 3, everything on the login screen and the desktop got smaller (still filled the screen, but the actual objects were smaller), but was very fuzzy and jittery, despite the fact that I chose the monitor's native resolution and refresh frequency when reconfiguring X. I could more or less use it, but it looked awful, and the monitor would usually give up and reject the signal after a few minutes - I could power the monitor off and then back on, and the fuzzy image would return. I ran the configuration utility while the graphics was messed up, and restarted X, but it didn't change anything apparent. 

I reset the driver in /etc/X11/xorg.conf back to "ati". The login screen and my desktop now display at 1024x768, so I'm back to where I started. As I mentioned above, no matter what I change, I never get a menu option for a higher resolution in the list under Applications > Settings > Display Settings.

The relevant parts (?) of my xorg.conf as it stands now are as follows:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. 3D Rage Pro AGP 1X/2X"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster 931B"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 3D Rage Pro AGP 1X/2X"
	Monitor		"SyncMaster 931B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by Honayo on 2007-03-04
Dermotti's tip solved my problem as well.
I was stuck at 640 x 480 until I followed the suggestions posted. Now I'm at 1024 x 768 in Edgy, on another machine, and loving it.:KS

---

### Post by vodsonic on 2007-03-07
Having been unable to use my monitor's native 1280x1024 resolution in Xubuntu by tweaking the xorg.conf myself, I decided to try booting to the Xubuntu live CD on the same computer, to see what kind of an xorg.conf was generated. 

As detailed in my post above, I installed Xubuntu on this box using a smaller, 1024x768 monitor, and now cannot get Xfce to utilize the greater resolution of my new monitor.

The relevant part of the xorg.conf generated when I booted to the live CD looks like this:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. 3D Rage Pro AGP 1X/2X"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 3D Rage Pro AGP 1X/2X"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

It's using the ati driver, and automatically included "1280x1024" at the head of the "Modes" fields.

BUT: The maximum resolution listed under Applications > Settings > Display Settings is still only 1024x768.

Does anybody have any suggestions for how I might get Xubuntu to utilize the full 1280x1024 resolution of my new monitor? If the live CD can't even autodetect the resolution and make it available, I'm not sure what to do at this point.

---

### Post by vodsonic on 2007-03-26
Bump.

Does anyone have any suggestions for solving the problem detailed above, i.e. getting Xfce/Xubuntu to give me the option of using the full resolution of my new monitor (1280x1024)?

I would love to accomplish this by tweaking a setting, rather than having to resort to reinstalling Xubuntu. (I ditched Windows and moved to Linux at least in part so I could avoid the frequent reinstalls.)

---

### Post by oldgoat on 2007-04-05
Have you tried running the live cd with the new monitor?  

If xubuntu correctly recognizes your new monitor you might be able to take a look at what is in xorg.conf while the live cd is running.

I have only seen this mentioned in the forums for other display problems - I have never had to use this approach.

---

