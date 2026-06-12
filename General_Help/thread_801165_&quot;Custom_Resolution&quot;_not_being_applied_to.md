---
title: "&quot;Custom Resolution&quot; not being applied to Login Screen"
date: 2008-05-20
forum: General Help
---

### Post by Jebtrix on 2008-05-20
Finally got my resolution problem fixed due to my KVM switch but the login screen does not obey the resolution settings. I'm curious to know why that is and how I can force the resolution to it also. 

Current xorg.conf mod:

[SIZE="1"]Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Acer"
	Modelname	"Acer AL1706"
	Horizsync	30.0-82.0
	Vertrefresh	50.0-75.0
        modeline  "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024_60.00"	
	EndSubSection
EndSection[/SIZE]

---

### Post by cdtech on 2008-05-20
SubSection     "Display"
        Virtual     1440 900
        Depth       24
        Modes      "1440x900" "1024x768"
    EndSubSection
EndSection

# Virtual --- Will affect your login screen.
# Modes --- Will affect your resolution once you log in.

Control+Alt+Backspace

OR, type in the terminal:
sudo /etc/init.d/gdm restart

Hope this helps....

---

### Post by Jebtrix on 2008-05-20
That didn't do the trick :( 
I wonder if its more Hardy weirdness.. dangit

---

### Post by Jebtrix on 2008-05-20
Just for others I tried to disable DCC in the device section. No worky there either. I don't quite understand the xserver part of the gdm.conf so I'm SOL at the moment.:confused:

---

