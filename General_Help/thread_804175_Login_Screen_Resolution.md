---
title: "Login Screen Resolution"
date: 2008-05-22
forum: General Help
---

### Post by Gripp on 2008-05-22
my log in screen resolution is way too high.  i get a warning message each time i log in and have no idea what it is saying becuase the text is too small...

i have tried changing the normal resolution and rebooting... didn't work...

i do remember from my way back 2004 gentoo manual bootstrap install that there is a file that states what the default res should be (along with all of the available modes and other monitor related settings)

i'm guessing that is what i need to change, but i have no idea what that file was...

---

### Post by FuturePilot on 2008-05-23
I think you might be looking for the /etc/X11/xorg.conf file. What graphics card do you have? Post the output of 
```
cat /etc/X11/xorg.conf
```

---

### Post by Gripp on 2008-05-23
EVGA nVidia 8800GTX

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection


---

### Post by Zorael on 2008-05-25
Change the Screen section to something like this.
```
Section "Screen"
	Identifier "Default Screen"
	Monitor "Configured Monitor"
	Device "Configured Video Device"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		**Modes	"1280x1024" "1024x768" "800x600" "640x480"**
	EndSubSection
EndSection
```
Pay special attention to the Modes line. The *first* listed resolution there will be the default, and as such, what's displayed at the login screen. The other resolutions will be available to users upon having logged in.

Add and remove resolutions there as you please.

---

### Post by mfearby on 2008-05-27
I've been trying to solve the same problem. I did look at my xorg.conf before but since it didn't list any resolutions, I assumed that maybe Ubuntu stores its resolutions elsewhere. However, I did edit my "Screen" section as per the following, and rebooted, but X is still starting up in 1280x1024 resolution at the login screen, even though I omitted this resolution completely:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768" "800x600"
	EndSubSection
EndSection
```

---

### Post by mfearby on 2008-05-27
I did find the following forum post which I thought might be useful, but it only changed the "usplash" resolution (I assume that's the correct term for the boot-up logo with the orange bar moving along) and the X login window loaded at 1280x1024 again :-(

[http://ubuntuforums.org/showthread.php?t=258484&highlight=resolution+login](http://ubuntuforums.org/showthread.php?t=258484&highlight=resolution+login)

I added  vga=0x318  to my kernel args but this didn't affect X.

---

### Post by Zorael on 2008-05-28
> **mfearby said:**
> I've been trying to solve the same problem. I did look at my xorg.conf before but since it didn't list any resolutions, I assumed that maybe Ubuntu stores its resolutions elsewhere. However, I did edit my "Screen" section as per the following, and rebooted, but X is still starting up in 1280x1024 resolution at the login screen, even though I omitted this resolution completely:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768" "800x600"
	EndSubSection
EndSection
```

What if you add "1280x1024" last? To explicitly give it a lower priority than 1024x768 and 800x600.

---

### Post by mfearby on 2008-05-28
Excellent suggestion but that didn't work, either :-(

Not sure if I've explained this before but I want to set the login resolution so that a teacher can demonstrate linux via a data projector to a classroom full of students.

---

### Post by Gripp on 2008-05-30
yeah, i still get some warning everytime i log in that i cant read... even inches from my screen... just too small..

hopefully it isn't important!

---

### Post by jpka on 2008-06-13
Please help with same problem.
I need setting which _exactly_ and _direct_ set resolution of login window
Reading ubuntuforums and other places, xorg.conf editing etc. is not solve this problem.
I have very specific xorg.conf, with each user resolution different from login window resolution.
First mode in "screen"-"display"-"modes" has ho effect.
User resolutions can be set by nvidia-settings, but it has no effect on login window.

Additionally, Ubuntu's Screen Resolutions GUI, even in 8.04, shows almost random resolutions in list, regardless of my 'noEDID' and 4 'modeline's in xorg.conf, which must _exactly_ gefine _this and only this_ resolutions available at all.

---

