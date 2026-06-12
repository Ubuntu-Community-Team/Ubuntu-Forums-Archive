---
title: "x1400 resolution"
date: 2007-03-13
forum: General Help
---

### Post by Praill on 2007-03-13
Hello Everyone,
I've looked all over this forum, and google for that matter, and havent found anyone with a similar problem. So here goes.

I have a Dell Inspiron 6400 equipped with an ATI radeon x1400. 
In windows I used the omega drivers and was able to run the laptop plugged into a VGA monitor in clone mode with one important feature: maintaining wide aspect ratio.

My external monitor is the standard 4:3 display and the laptop screen is wider (8:5). With the omega driver (in windows) I could check the option "maintain wide aspect ratio" and it would create the 1280x800 resolution on my 4:3 monitor by upping the resolution (probably to 1280,1024) and only drawing 800 of the 1024 available y pixels in the middle of the screen.

This is a very important feature to me, and I see no way to duplicate it in linux. Currently, to use the external monitor, I have to set the resolution to 1024x768 since its the largest 4:3 option in the gnome utility (1024x768 is unbearably large). If I try to use any widescreen format I get an out of range error from the external monitor.

Any help would be greatly appreciated.

PS. I have installed and am using the ATI module, so its not a vesa problem.

---

### Post by Praill on 2007-03-13
Upon further searching I found this to be a common and rather complicated question, so I'm not surprised I didn't get any replies.
I have figured out a solution I deem to be "good enough" however and will post it here for others that stumble upon this post. This may seem obvious to alot of people, but I learned something today about the xorg.conf and how the ati driver modifies and reads from it. This applies to those of us that have ati cards and are using the proprietary ati driver.

You may notice that after you ran aticonfig --inital you have two entries for monitor, device and screen in your xorg.conf file.
ex.
```
Section "Monitor"
	Identifier   "Generic Monitor"
	ModeLine     "1280x1024" 154.0 1920 1968 2000 2080 1200 1203 1209 1235
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1280x800" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

I, like many people I'm sure, noticed this but was never brave enough to mess with it as long as it was working. However, I found out that first selection for each is what the X server was using prior to you installing the driver, and the second section is what the driver is using after.
Since ATI's installer SUCKS, it doesnt ask you to optimize resolutions and just gives you hardware defaults. Therefore you have to manually add all your mode subsections into the Screen section with the aticonfig-Screen[0] identifier. If you change the mode subsections in the Screen section with the "Default Screen" identifier it does nothing.
Add all your resolutions to the right section
ex.
```
Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
SubSection "Display"
		Depth     1
		Modes    "1600x1280" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	SubSection "Display"
		Depth     24
		Modes    "1600x1280" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

and when you restart X the gnome resolution tool (System-->Preferences-->Screen Resolution) should be updated with your entered values, assuming your card supports them.

Good Luck. Hopefully this helps someone.

---

### Post by elephant007 on 2007-03-18
> **Praill said:**
> Upon further searching I found this to be a common and rather complicated question, so I'm not surprised I didn't get any replies.
I have figured out a solution I deem to be "good enough" however and will post it here for others that stumble upon this post. This may seem obvious to alot of people, but I learned something today about the xorg.conf and how the ati driver modifies and reads from it. This applies to those of us that have ati cards and are using the proprietary ati driver.

You may notice that after you ran aticonfig --inital you have two entries for monitor, device and screen in your xorg.conf file.
ex.
```
Section "Monitor"
	Identifier   "Generic Monitor"
	ModeLine     "1280x1024" 154.0 1920 1968 2000 2080 1200 1203 1209 1235
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1280x800" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

I, like many people I'm sure, noticed this but was never brave enough to mess with it as long as it was working. However, I found out that first selection for each is what the X server was using prior to you installing the driver, and the second section is what the driver is using after.
Since ATI's installer SUCKS, it doesnt ask you to optimize resolutions and just gives you hardware defaults. Therefore you have to manually add all your mode subsections into the Screen section with the aticonfig-Screen[0] identifier. If you change the mode subsections in the Screen section with the "Default Screen" identifier it does nothing.
Add all your resolutions to the right section
ex.
```
Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
SubSection "Display"
		Depth     1
		Modes    "1600x1280" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	SubSection "Display"
		Depth     24
		Modes    "1600x1280" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

and when you restart X the gnome resolution tool (System-->Preferences-->Screen Resolution) should be updated with your entered values, assuming your card supports them.

Good Luck. Hopefully this helps someone.

I did the second part as instructed and let's just say I had to learn how to use the VI in the recovery console... I would not recommend using this suggestion... if you do use it, learn VI first!! HA HA
I had to use VI to remove the data that was changed... I am back up and running in X now

---

### Post by Praill on 2007-03-19
Yes, its always a good idea to backup your xorg.conf before messing with it. Then you can boot into recovery mode and just do sudo cp <backed up file> <actual file>
Im surprised it didnt work. Just adding resolution modes should not crash X. It might be trying to use a defualt resolution that either isnt listed or isnt supported by the monitor.
the command: dpkg-reconfigure xserver-xorg will allow you to start with a fresh xorg.conf file. I believe one of the options is to set default resolution.

---

