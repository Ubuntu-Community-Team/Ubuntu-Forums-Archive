---
title: "Low Resolution Problem"
date: 2007-06-18
forum: General Help
---

### Post by dror_trieman on 2007-06-18
Hello All ;)

I'm nob in UBUNTU, at the moment very pleased.

I have annoying problem with the screen resolution.

My computer has Radeon 9200, downloaded the drivers from ATI website, 

but still, the largest resolution possible from the System->Preferences-> Screen Resolution

is 800X600.

How can I fix it?

Thanks :)

---

### Post by longlegs on 2007-06-18
Hi ,
I'm a newbie too but had te exact reverse of your problem. The lowest resolutio I had was 1600xXXX
The solution is the same for both problems. You need to edit the xorg.conf file.
CAUTION MAKE NO TYPO"S. I can't tell you how to recover if xorg.conf is corrupted.
open a terminal. In Feisty you click on accessories=>terminal
at the prompt, type sudo gedit /etc/X11/xorg.conf
thats a capital X one one
press enter then enter your password. The text editor 'gedit' will open the xorg.conf for editing.
You will look for a series of line similar to these
====================================================
Section "Monitor"
	Identifier	"PF790-2"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc 3D Rage Pro AGP 1X/2X"
	Monitor		"PF790-2"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "1280x1024" "1152x864" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "1280x1024" "1152x864" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "1280x1024" "1152x864" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "1280x1024" "1152x864" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "1280x1024" "1152x864" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "1280x1024" "1152x864" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

==========================================================
the resolutions that you will have in System=>preferences=>screen resolution depend on the 
resolutions in these lines. NOTE the I placed my desired default resolution first, and the others afterward. This causes my login screen to be the same as my working resolution. Enter the resolution choices that you want, in every line, TRIPLE CHECK that you have made no other changes.
Now look at the "Screen" section. you should change the sync and refresh rates to what your monitor and video card will support but not greater. In my case 60 is the max refresh rate.

When you are done, save the changes, overwriting the original.
reboot. CHeck system=>preferences=>resolution to verify that this fixes your problem.

Good luck,
longlegs

---

### Post by phr0ze on 2007-06-18
THis is the area most people get wrong and its the one that controls resoultion...

HorizSync 28-64
VertRefresh 43-60

Also the 1st reply is wrong,type:
gksudo gedit /etc/X11/xorg.conf

don't use sudo for graphical programs.

---

### Post by racso39 on 2007-06-18
Oh my God!

Thanks for the note on the Sync thing, I spent hours and hours and hours trying to get my resolution 1280x1024 I had in Windows here in Ubuntu. I finally installed drivers right via Envy but still no resolution so I once again edited the xorg and it looks like this now:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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


Then I rebooted GNOME (ctrl+alt+backspace) and voila! (funny, look at me how I am talking, and I am so N00B at this, I mean I installed ubuntu yesterday for the first time in my life)

I got some more issues but for now I am going to take a break.

---

### Post by longlegs on 2007-06-19
Hi phr0ze,
> **phr0ze said:**
> 

Also the 1st reply is wrong,type:
gksudo gedit /etc/X11/xorg.conf

don't use sudo for graphical programs.

As I said, I too am a newbie, and have not heard of the 'gksudo' command. I have used only sudo .....     What exactly is the difference, if both work for editing a text file?
Thanks
longlegs

---

### Post by phr0ze on 2007-06-19
There is lots of info on the usage of gksudo and sudo. 

A general rule: If a new window will pop up from the command you should use gksudo. If the command will run in the existing window use sudo. You'll just have to get used to knowing which commands open a new window.

OP:
I'm glad your problems are solved.

---

### Post by RedSquirrel on 2007-06-19
A couple of links...

For sudo/gksudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

For resolution issues:
[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

---

### Post by wxman on 2007-06-19
> **dror_trieman said:**
> Hello All ;)

I'm nob in UBUNTU, at the moment very pleased.

I have annoying problem with the screen resolution.

My computer has Radeon 9200, downloaded the drivers from ATI website, 

but still, the largest resolution possible from the System->Preferences-> Screen Resolution

is 800X600.

How can I fix it?

Thanks :)

Could you PLEASE tell me where you got the driver, it's file name, etc? Also any instructions to go with it all.

I must have tried a hundred different searches for info on how to fix mine, but none have worked. I have the same problem as you, low resolution. I downloaded some sort of install file from ATI, but it didn't work, and it had no instructions. I'm not a complete computer idiot, but I'm still learning Linux, and it's frustrating when the instructions assume you know what you're doing.

Thanks.

---

### Post by racso39 on 2007-06-20
> **wxman said:**
> Could you PLEASE tell me where you got the driver, it's file name, etc? Also any instructions to go with it all.

I must have tried a hundred different searches for info on how to fix mine, but none have worked. I have the same problem as you, low resolution. I downloaded some sort of install file from ATI, but it didn't work, and it had no instructions. I'm not a complete computer idiot, but I'm still learning Linux, and it's frustrating when the instructions assume you know what you're doing.

Thanks.


Try getting Envy package and install it, it will do all the work for you:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Just like you, I am not a complete idiot, but I just have 3 days using Linux. After you install the drivers and still can't get the resolution you want, just read above, the first 2 post in this thread.

---

### Post by wxman on 2007-06-20
> **racso39 said:**
> Try getting Envy package and install it, it will do all the work for you:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Just like you, I am not a complete idiot, but I just have 3 days using Linux. After you install the drivers and still can't get the resolution you want, just read above, the first 2 post in this thread.

I did try the Envy package, and after it did the install of the ATI driver, the whole system wouldn't reboot. I had to revert back to what I had before to make anything work.

---

