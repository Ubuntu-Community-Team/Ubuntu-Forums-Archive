---
title: "Desktop effects not working!"
date: 2008-06-14
forum: General Help
---

### Post by simpsonsfreak on 2008-06-14
Hi all,

I have a problem. I had advanced desktop effects with Compiz working before on my laptop, but now after I've tried to get an external monitor working I can't get compiz to work again or anything more than basic desktop effects. Can anyone help me? This is the output that I get when I try to start compiz:

hayden@hayden-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

Thanks :)

---

### Post by Forlong on 2008-06-14
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

Post the output here.

---

### Post by simpsonsfreak on 2008-06-14
> **Forlong said:**
> [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

Post the output here.

Here we go:

```
 ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 7.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         vesa
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```

Thanks

---

### Post by simpsonsfreak on 2008-06-14
Anyone?

---

### Post by jp734 on 2008-06-14
You need to install the right driver for your video card. Desktop effects will not work with vesa driver

---

### Post by simpsonsfreak on 2008-06-14
> **jp734 said:**
> You need to install the right driver for your video card. Desktop effects will not work with vesa driver

I thought so, but I had it working before on this computer with the same driver I'm sure. Would anyone be able to tell me which driver to use?

---

### Post by nkri on 2008-06-14
post your graphics card specs (brand, model, etc.) and we'll see what we can do about a driver.  If you're not sure about the specs, post the output of:
```
lspci
```

---

### Post by simpsonsfreak on 2008-06-14
> **nkri said:**
> post your graphics card specs (brand, model, etc.) and we'll see what we can do about a driver.  If you're not sure about the specs, post the output of:
```
lspci
```

Here it is:

```
hayden@hayden-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
0a:06.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:06.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```

---

### Post by nkri on 2008-06-14
okay.  First, we need to get to Screens and Graphics Preferences:
```
gksu displayconfig-gtk
```

A window should pop up showing your display settings.  Go to the Graphics Card tab, and click the bar next to "Driver."

The driver you need is "i810 - Intel Integrated Graphics Chipset..."

Select this from the list in "choose driver by name," and click OK.
Click OK again, and try to enable the desktop effects.  If it doesn't work immediately, try rebooting and see what happens.

Good luck!

---

### Post by simpsonsfreak on 2008-06-14
> **nkri said:**
> okay.  First, we need to get to Screens and Graphics Preferences:
```
gksu displayconfig-gtk
```

A window should pop up showing your display settings.  Go to the Graphics Card tab, and click the bar next to "Driver."

The driver you need is "i810 - Intel Integrated Graphics Chipset..."

Select this from the list in "choose driver by name," and click OK.
Click OK again, and try to enable the desktop effects.  If it doesn't work immediately, try rebooting and see what happens.

Good luck!

Thanks, I tried that but for some reason it keeps on reverting back to vesa. How come?

---

### Post by nkri on 2008-06-14
Sorry this took so long, but you actually need to do two things for it to work:
Once you get to the "Driver" bar, click on "Choose driver by model" instead of "Choose driver by name."
Go to Intel, then click 945.
click ok, and ok again.
it should give you a window that says "all users should log off for the changes to take effect."

Good luck!

---

### Post by simpsonsfreak on 2008-06-14
> **nkri said:**
> Sorry this took so long, but you actually need to do two things for it to work:
Once you get to the "Driver" bar, click on "Choose driver by model" instead of "Choose driver by name."
Go to Intel, then click 945.
click ok, and ok again.
it should give you a window that says "all users should log off for the changes to take effect."

Good luck!

Nope, doesn't work. :( When I logout it says it is running in low graphics mode because it can't detect my screen, and then it switches back to vesa again.

---

### Post by nkri on 2008-06-14
I see what you mean...I just tested it out (the opposite way, using the vesa instead if Intel) and got the same response of reverting back.:confused:

I find this kinda weird, since only about a month ago when I had this same problem in 7.10, it was very easy to fix.

Hmmm...have you tried restarting after changing it the way I said before?  I dunno if this'll do anything different, but it sometimes does...computers:mad:

I'm going to bed right now, but I'll check back again sometime tomorrow and try to help some more.

---

### Post by simpsonsfreak on 2008-06-14
> **nkri said:**
> I see what you mean...I just tested it out (the opposite way, using the vesa instead if Intel) and got the same response of reverting back.:confused:

I find this kinda weird, since only about a month ago when I had this same problem in 7.10, it was very easy to fix.

Hmmm...have you tried restarting after changing it the way I said before?  I dunno if this'll do anything different, but it sometimes does...computers:mad:

I'm going to bed right now, but I'll check back again sometime tomorrow and try to help some more.

Yep, I tried restarting. I've had this problem for quite a while now. :(

Thanks for your help so far, hopefully we can fix it!

---

### Post by Forlong on 2008-06-15
> **simpsonsfreak said:**
> Anyone?
Please don't push your threads after such a short time, that is regarded as highly impolite.


Please post your /etc/X11/xorg.conf

---

### Post by jp734 on 2008-06-15
I had the same problem before. I was using an unofficial driver for my matrox g550 and for some reason, one time it would not detect my card when it worked perfectly for a long time. So it used the vesa driver. For me to fix the problem, I had to reinstall the xorg driver and when I got it to work, I again reinstalled the unofficial driver since it supports the 3d acceleration I need. Working perfectly again since then. Hopefully that will do the trick for you.

---

### Post by nkri on 2008-06-15
Well, after searching around for a while, I think I might have found what we've been looking for: the instructions from DizzyTech at the bottom of the page of [_this_]("http://ubuntuforums.org/showthread.php?t=420726&page=2") thread might help quite a bit, and like Forlong said, it would be good if you post your xorg.conf if there is a problem.

---

### Post by simpsonsfreak on 2008-06-16
> **nkri said:**
> Well, after searching around for a while, I think I might have found what we've been looking for: the instructions from DizzyTech at the bottom of the page of [_this_]("http://ubuntuforums.org/showthread.php?t=420726&page=2") thread might help quite a bit, and like Forlong said, it would be good if you post your xorg.conf if there is a problem.

This is becoming a real PITA. I tried that, but it still keeps switching back to vesa :mad:

Here's my xorg.conf:
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by Forlong on 2008-06-16
You are using a failsafe xorg.conf

Try this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then reboot and try again.

---

### Post by simpsonsfreak on 2008-06-17
> **Forlong said:**
> You are using a failsafe xorg.conf

Try this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then reboot and try again.

This is so annoying. I finally got it working - but now the computer is slower than it has ever been before. I couldn't even get into Firefox, I've had to post this from another computer.

So, no luck, I'll prefer for my computer to be at least useable than have some effects.

---

### Post by nkri on 2008-06-17
That sucks.  Well, maybe when 8.10 comes out, you could try again and see what happens?  New distros usually have a lot of fixes and improvements.

---

