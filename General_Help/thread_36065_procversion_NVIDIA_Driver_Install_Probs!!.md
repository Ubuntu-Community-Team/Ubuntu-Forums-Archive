---
title: "/proc/version NVIDIA Driver Install Probs!!"
date: 2005-05-21
forum: General Help
---

### Post by hammett111 on 2005-05-21
Okay, I will start by saying Windows is Dead for me I'm completely converted to Linux!!

However I have made a little Boo Boo. I downloaded the latest NVIDIA drivers 7174 and tried to install them. Ufortunately I get these faults -

1.  /proc/version "cannot find directory. Directory does not exist"

In my ignorance I proceeded past this point, and it could'nt find a precompiled kernel interface, so it tried to compile its own. Woe is me, for it then returned cannot find gcc compiler, do you wish to continue. ONCE AGAIN!! in my ignorance I continued with the installation. It then returned, "cannot continue with installation." It then tries to uninstall itself, but it can't do an entire install. When I reboot it won't start X, it only will if I change "nvidia" in the xorg.conf to "nv" - however this leaves me with absoltuely CRAP performace when I return to X. 

Question? Can anyone help me fix this problem, AKA!! install the 7174 drivers I downloaded?
Or uninstall the current Nvidia setup and reinstall the Synaptic driver sets?

I have currently installed the 2.6.11-1-amd64-k8 Kernel. 

Cheers Ubuntu Noob!

---

### Post by FreeEagle on 2005-05-21
Hi there, 

i will help you in this matter to solve all your Problems.

First of all you have to set you Repo. and this can be done be following this Procedure :
[http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto](http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto)

then after this go to your Synaptic and refresh it first then go to search option and write Nvidia and install the Nvidia Driver from there. ( install this nvidia-glx  and this nvidia-settings )
After that do a Restart and then 
run this command in a Shell:  sudo nvidia-glx-config enable

after that he will ask you about your Password, just put the Password and restart your pc and done .

thats it.

For more information you can read this : 
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)


Best Regards,
 FreeEagle

---

### Post by hammett111 on 2005-05-21
[QUOTE=FreeEagle]Hi there, 

i will help you in this matter to solve all your Problems.

First of all you have to set you Repo. and this can be done be following this Procedure :
[http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto](http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto)

then after this go to your Synaptic and refresh it first then go to search option and write Nvidia and install the Nvidia Driver from there. ( install this nvidia-glx  and this nvidia-settings )
After that do a Restart and then 
run this command in a Shell:  sudo nvidia-glx-config enable

after that he will ask you about your Password, just put the Password and restart your pc and done .

thats it.

For more information you can read this : 
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)


Best Regards,
 FreeEagle[/QUOTE]
 Sorry I've tried it before and it didn't work. I installed the nvidia stuff using apt-get install and then changed my xorg.config "nv" to "nvidia" I can make it to X laoding but it freezes. I can only load into the gnome desktop when "nvidia" is changed to "nv". This is my xorg.conf:

# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel"		"true"
	Option		"NvAGP"			"1"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-90
	VertRefresh	50-75
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by hammett111 on 2005-05-21
Thanks My Man But I have solved my Problem and have pretty much got Nvidia Cooked!! I'm available to help anyone with Nvidia problems, so just throw your questions my way and I'll smokem for ya!!!

---

### Post by FreeEagle on 2005-05-22
happy that you did it yourself....

But can you tell us what have you done to solve it, if you do not mind :)


FreeEagle

---

### Post by hammett111 on 2005-05-23
Okay I booted into X using the "nv" instead of "nvidia" change. Then I uninstalled all the nvidia crap I downloaded via synaptic and reinstalled it. I rebooted and when it went into X I changed "nv" to "nvidia" and rebooted again......and Hellalujah the Gods of Linux blessed my sorry butt!!!

I then tweaked my xorg.conf file again deleting "dri" ensuring "glx" was there, added:

Option                   "RenderAccel"   "true"
Option                   "NvAGP"             "3"

And Home sweet home for me. Is that good enough or do you anything else?

---

