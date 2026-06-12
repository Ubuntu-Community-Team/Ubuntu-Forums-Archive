---
title: "making the monitor display at 100hz..."
date: 2005-10-26
forum: General Help
---

### Post by fargoth on 2005-10-26
my monitor is philips brilliance 109P2, and it should display 1280x1024@100hz..
but then i click on screen resolution on the system->preferences it only shows 85 75 and 60....
xorg.conf recognized my screen and my video card correctly i think...

```
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"PHILIPS 109P"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600]"
	Monitor		"PHILIPS 109P"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1792x1344" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

any ideas?
i got used to my 100hz and now 85hz flickers... =(

---

### Post by fargoth on 2005-10-27
i really need to set the monitor to 100hz, my eyes hurt... please tell me how to unlock this refresh rate...

---

### Post by mykey on 2005-10-27
[QUOTE=fargoth]i really need to set the monitor to 100hz, my eyes hurt... please tell me how to unlock this refresh rate...[/QUOTE]
In the monitor section first set values for HorizSync and VertRefresh e.g
HorizSync   30-92
VertRefresh 50-160
these are for a Phillips 109S - check out what your monitor supports via google

If this does not give you the Frequency you like go look for modeline modifiers for your resolution - these are supposed to be added to the monitor section too and look like this:
```
   Modeline "1152x864/84Hz" 135 1152 1464 1592 1776 864 864 876 908
    Modeline "1152x864/78Hz" 110 1152 1240 1324 1552 864 864 876 908
    Modeline "1152x864/99Hz" 137.65 1152 1184 1312 1536 864 866 885 902
```
 - good luck -

---

### Post by fargoth on 2005-10-27
thanks, i'll try that. 
by the way, what does the numbers after the "1152x864/84Hz" mean, how do i know what numbers to write there?

---

### Post by mykey on 2005-10-27
no idea - they have been working for me for a long time though and I forgot where I got them originally

---

### Post by heimo on 2005-10-27
[quote=fargoth]thanks, i'll try that. 
by the way, what does the numbers after the "1152x864/84Hz" mean, how do i know what numbers to write there?[/quote]

You can use gtf or this page to generate modelines:
[http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

For example:```

 # 1280x1024 @ 100.00 Hz (GTF) hsync: 108.50 kHz; pclk: 190.96 MHz
  Modeline "1280x1024_100.00"  190.96  1280 1376 1520 1760  1024 1025 1028 1085  -HSync +Vsync
```
Some related instructions:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

