---
title: "cant change resolution even modify xorg.conf"
date: 2008-02-08
forum: General Help
---

### Post by efecanerdur on 2008-02-08
I tried all the manual and howtos but it doesnt work for me. I am on linuxmint. I modify xorg.conf and added 1152x864, 1280x960 after that i restarted x server but resolutions that i added dont appear in resolution list. I also modified HorizSync to 30-70 and VertRefresh to 50-150. My monitor's "[Samsung 793DF]("http://www.samsung.com/my/products/monitor/archivedmonitor/793df.asp")"

So whats the problem. Thanks.

---

### Post by DJiNN on 2008-02-08
What video card do you have in your machine? :)

---

### Post by efecanerdur on 2008-02-08
An onboard vga "NVIDIA GeForce 6100 GPU 256 MB" on BIOSTAR NF61S GF6100.

---

### Post by DJiNN on 2008-02-08
> **efecanerdur said:**
> An onboard vga "NVIDIA GeForce 6100 GPU 256 MB" on BIOSTAR NF61S GF6100.

That's good news..... :)  There's a small app called "Envy" and if you go [here]("http://www.albertomilone.com/nvidia_scripts1.html") you can have a read about what it is & what it does. 

Then either download the Ubuntu .deb file from the Downloads section of the Envy site (& install) or run Synaptic Package manager search for Envy & install from there. Then run Envy & that should pretty much take care of things for you. It's a great tool for both nVidia & ATi cards, and i used it only the other day with great success, on pretty much the same card (Onboard nvidia) that you have. :)

Let me know how it goes, and please make sure to follow whatever instructions are on the website for your particular set up, because depending upon what drivers you already have installed & what hardware etc, you may have to follow certain steps & procedures.

---

### Post by efecanerdur on 2008-02-08
Envy already installed. I ran envy but at the end the following error occured
[[IMG]http://img206.imageshack.us/img206/7619/screenshotqs5.th.png[/IMG]](http://img206.imageshack.us/img206/7619/screenshotqs5.png)

---

### Post by forrestcupp on 2008-02-08
In my opinion, Envy is more useful for ATI cards because the ATI drivers in the repos are way behind the current ones.  But if I had an nVidia card, I would use Ubuntu's Restricted Drivers Manager instead.  Open up the RDM and see if it gives you the option to install restricted drivers for your geforce.  If that works, make sure you install the nvidia settings app:
```
sudo apt-get install nvidia-settings
```
That settings app should allow you to set your resolution.

---

### Post by DJiNN on 2008-02-08
> **efecanerdur said:**
> Envy already installed. I ran envy but at the end the following error occured
[[IMG]http://img206.imageshack.us/img206/7619/screenshotqs5.th.png[/IMG]](http://img206.imageshack.us/img206/7619/screenshotqs5.png)

Sorry to hear that. Envy worked fine for me and saved me a lot of hassle. 

Anyway, can you post your xorg.conf file?  It may help to hopefully solve the problem.

---

### Post by efecanerdur on 2008-02-09
```
Section "Files"
	# path to defoma fonts
	FontPath "/usr/share/fonts/X11/misc"
	FontPath "/usr/share/fonts/X11/cyrillic"
	FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath "/usr/share/fonts/X11/Type1"
	FontPath "/usr/share/fonts/X11/100dpi"
	FontPath "/usr/share/fonts/X11/75dpi"
	FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load "bitmap"
	Load "ddc"
	Load "dri"
	Load "extmod"
	Load "freetype"
	Load "glx"
	Load "int10"
	Load "vbe"
EndSection

Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "CoreKeyboard"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "tr"
	Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ImPS/2"
	Option "ZAxisMapping" "4 5"
	Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier "stylus"
	Driver "wacom"
	Option "Device" "/dev/input/wacom"
	Option "Type" "stylus"
	Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier "eraser"
	Driver "wacom"
	Option "Device" "/dev/input/wacom"
	Option "Type" "eraser"
	Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier "cursor"
	Driver "wacom"
	Option "Device" "/dev/input/wacom"
	Option "Type" "cursor"
	Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
	Identifier "Generic Video Card"
	Driver "vesa"
	BusID "PCI:0:13:0"
	Option "UseFBDev" "true"
EndSection

Section "Monitor"
	Identifier "Generic Monitor"
	HorizSync 30-70
	VertRefresh 50-160
	Option "DPMS"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "Generic Video Card"
	Monitor "Generic Monitor"
	DefaultDepth 24
	SubSection "Display"
		Depth 1
		Modes "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Default Screen"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
	InputDevice "stylus" "SendCoreEvents"
	InputDevice "cursor" "SendCoreEvents"
	InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode 0666
EndSection
```

@forrestcupp
It outputs the following:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  g++-4.1: Depends: libstdc++6-4.1-dev (= 4.1.2-0ubuntu4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

