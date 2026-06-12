---
title: "Bit of a problem with nVidia drivers..."
date: 2007-09-13
forum: General Help
---

### Post by hyrule_man on 2007-09-13
Well, I installed some nVidia drivers in restricted driver manager, to play some games. (Halo, Open Arena, Alien Arena 07, etc.) Well, the games all work great, but my default resolution on my desktop is HUGE. And its frankly quite annoying to reboot into my drivers every time i want to play a game. So, any solutions? (Oh, and when I try to change my resolution, my only option is the default huge one....)

---

### Post by hyrule_man on 2007-09-13
Bump.

---

### Post by Technophobia on 2007-09-13
I have a few ideas assuming that you cant set   System > Prefs > Screen resolution

1) try editing your xorg.conf file and remove all unwanted screen resolutions.


2) Use a this program called Envy to install / uninstall your gfx drivers. Envy also installs the control panel for your graphics card  which might help you with your bre.. resolution reduction problem. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)


Number two would be your best choice if you have no knowledge of editing your xorg.conf.


good luck

---

### Post by fragos on 2007-09-13
People have mixed luch using any installation tools not in the Ubuntu repositories.  IMHO, stay away from the likes of envy and automatix.  When you properly installed the Nvidia drive, as you did, you also get nvidia-settings which you can run from a terminal.  It's thankfully a GUI program.  "X Server Display Configuration" has resolution.  If you wish to edit /etc/X11/xorg.conf here's my screen related configuration for reference.

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Viewsonic VA1912wb"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Viewsonic VA1912wb"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by hyrule_man on 2007-09-13
Well.. Envy didn't work, and I'm too nervous to edit my xorg.conf.. lol Bump?

---

### Post by hyrule_man on 2007-09-13
*Sigh...* Bump..

---

### Post by maybeway36 on 2007-09-13
You could use:
```
sudo dpkg-reconfigure xserver-xorg
```
In the first step, make sure the driver "nvidia" is selected. There is also a screen resolution step near the end. For everything else, use the defaults.

---

### Post by hyrule_man on 2007-09-15
Ok, I'm at the Resoluion step.. But how do I check/uncheck things..? Lol.

---

### Post by hyrule_man on 2007-09-15
Oh, ok, you hit space.. Anyways, it didn't work...... Still, my only selectable res. is 800x600.

---

### Post by Stan_1936 on 2007-09-15
I got this method to work:
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

### Post by hyrule_man on 2007-09-15
Omg, DIDNT WORK. Maybe I should just get a new card... How are Ubuntu's ATI drivers? Oh, and a bit off topic, is the Automatix website down or what? Its been offlne for like 2 days now...

---

### Post by Crafty Kisses on 2007-09-15
> **hyrule_man said:**
> Omg, DIDNT WORK. Maybe I should just get a new card... How are Ubuntu's ATI drivers? Oh, and a bit off topic, is the Automatix website down or what? Its been offlne for like 2 days now...

Don't go with ATI, they really don't support Linux. remember always stick with NVIDIA if you have Linux.

---

### Post by hyrule_man on 2007-09-15
Argh..

---

