---
title: "2 Hopefully easy proplems."
date: 2007-12-14
forum: General Help
---

### Post by ThomasWii on 2007-12-14
Hi, I've got 2 problems, (I'm only a kid, so try and answer as simply as possible.)

1) I can't connect to my wireless Internet, i don't know why or what make my wireless card thingy is. But what i do know is the the router is Netgear (Provided by Sky) and are security is 64bit WEP.

2) I have a laptop with the screen res of 1280x800, but in the drop down list it only has 800x600 and 640x840, i have tried the xorg.conf thing, and that did not work and i have tried the dpkg-reconfigure xserver-xorg thing and that didn't work.

Edit: I'm using 7.04


Thanks in advance.

Thomas

---

### Post by Joshua on 2007-12-14
For wireless, it might help if we could figure out what kind of card you use.  Is it in a desktop or the laptop from your second question?  Is it a card, built in, or a USB adaptor?  Or if it came with the computer, what kind of computer is it?  Are you using Gutsy (Ubuntu version 7.10)?  If so, when you click on the the network icon in the top right corner does the wireless option show up?  Also, if you open terminal (in the Applications menu) what is the result of:

```
ifconfig
```
and
```
iwconfig
```

For the resolution, what kind of graphics do you have (or what kind of laptop is it)?  And when you did

```
dpkg-reconfigure xserver-xorg
```

You checked off your prefered resolutions in the list that it gave you?

Now-a-days it's usually possible to get the wireless and graphics working pretty well even if they aren't working out of the box.

---

### Post by ThomasWii on 2007-12-14
all i know is it's a laptop and I'm running 7.04, it's not a usb one,

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:14:0B:01:73:1B  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bff:fe01:731b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16419 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17379330 (16.5 MiB)  TX bytes:1913923 (1.8 MiB)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2191 (2.1 KiB)  TX bytes:2191 (2.1 KiB)
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

with the res, i didn't understand the dpkg-reconfigure xserver-xorg thing

---

### Post by r-mo on 2007-12-14
> **ThomasWii said:**
> with the res, i didn't understand the dpkg-reconfigure xserver-xorg thing

If you run it with the -phigh switch it'll just ask you to select what resolutions your monitor supports. So try this command and see if it helps

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

You'll need to restart the computer (or X) after you've run it.

---

### Post by r-mo on 2007-12-14
As for your wireless this is probably not going to be easy.  By the looks of things you have a broadcom 4318 card.  See this thread for help

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by Joshua on 2007-12-14
Well, it looks to me like your wireless card is being recognized and just needs to be set up to work with your router.  Just to be sure, what is the output of:

```
lspci | grep Broadcom\ Corporation
```
(this should say if the computer thinks you have a Broadcom card, and what model it is)
and
```
lsmod | grep bcm43xx
```
(lsmod will list all the modules that you have running, and this command should filter it to see if the module for the Broadcom 4318 is set up)

If it just needs to be set up, can you select your home's wireless network from the network manager list (I think the network manager icon is in the top right corner of the screen)?  Does it ask for a password when you select your network?

For the resolution, when you run
```
dpkg-reconfigure xserver-xorg 
```
in the terminal, after you go through several screens, it should ask you to select the resolutions that you want to use, and give you a scrollable list from which to choose.  You can use the arrow keys to highlight the ones you want and then hit the spacebar to put a check next to them.  After you select all the ones you want, you hit tab to highlight the "ok" option (or maybe it says "next" or something).  And hit enter to continue.

If you never get the option to select the resolutions, there should be an option early on to choose a basic or advanced configuration.  Choose the advanced configuration mode and you should be asked more detailed questions after that.  Also, when it asks about autodetecting, say no.  If there is anything that you don't know, just hit enter, or choose the button to continue, and it should leave that question in the previous configuration.

After you make all the selections you can restart the the xserver by hitting <alt>+<ctrl>+<backspace>, or by restarting.  Changes won't take effect until the xserver is restarted.

Also, before you reconfigure stuff, you should do this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
and enter the password.

Then if you (you should write this part down), if you restart your computer or the xserver and the graphical login doesn't come back you can do this from the command prompt:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
to get your original configuration back.  Then restart again, or type:
```
startx
```
And the graphical login should be back.

---

### Post by Joshua on 2007-12-14
After looking at what r-mo sent, maybe wireless will be harder than I thought, but ndiswrapper isn't to difficult to use, and an upgrade to Gutsy might solve the problem outright.

---

### Post by Joshua on 2007-12-14
After looking at what r-mo sent, maybe wireless will be harder than I thought, but ndiswrapper isn't to difficult to use, and an upgrade to Gutsy (7.10) might solve the problem outright.

---

### Post by ThomasWii on 2007-12-14
Thank you for helping, my screen res is right, and i can connect to the Internet. I am very happy now:)

Long live Ubuntu

Thomas

---

### Post by Joshua on 2007-12-14
Hmmm... it just started working?  It's a Christmas MIRACLE!:)

---

### Post by ThomasWii on 2007-12-19
Sorry, but it gone wrong again, it gone back to 800x600. I've tried what you said, but that dose not work.

Here's the xorg.conf file.
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Thanks in advance,

Thomas

---

### Post by ThomasWii on 2007-12-19
Come on guys, i really need help.

---

### Post by ThomasWii on 2007-12-19
Also when it starts up it says the it is running in safe graphics mode.

---

### Post by lswest on 2007-12-19
the xorg.conf is right as far as i can see, the problem is that it's running in safe graphics mode, which means that some setting is either a) too much for your card  b) the driver has been disabled/messed up  or c) it's just on the fritz lol.  honestly the only advice i can give you is to try the dpkg-reconfigure command again, or to (if you have an nvidia card with the nvidia drivers installed) install the package nvidia-settings ```
 sudo apt-get install nvidia-settings
``` after the install run ```
nvidia-settings
``` and change the resolution to auto.  **the package name might be wrong, if it says the package cant be found, search for it with [sudo apt-cache search nvidia settings[/code] and pick the entry that describes an nvidia control panel.

---

### Post by Joshua on 2007-12-19
Hmmm... from what I understand about "Safe Graphics Mode" it is a new thing in Gutsy where the system can automatically detect that your current graphics configuration is bad, but rather than dump you to a command line terminal, it will load very basic and "safe" graphics settings so that you can still use the normal desktop.  Maybe someone can give more detail about "Safe Graphics Mode"???

But by the looks of it, that's probably why you can only set it to 800x600.  You can try this:

```
gksudo gedit /etc/X11/xorg.conf
```

Edit this section
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection
```

So that Driver is "vesa" instead of "sis".

That may get you better resolutions, but I doubt that it is ideal.  If you have a newer laptop, you've probably got some advanced capabilities in the graphics area that vesa won't provide.  Anyone know how he can find out what kind of graphics he has?  A laptop brand and model number would be good.  But you would need that info to make sure you use the right driver.

---

### Post by Joshua on 2007-12-19
As far as the comments from lswest, Gutsy handles that pretty well with the restricted drivers application.

Do you have Gutsy or Feisty?  You can find out by doing:

```
uname -a
```

---

### Post by ThomasWii on 2007-12-19
when i put in ```
uname -a
```it comes up with ```
Linux thomas-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

```

and....```
gksudo gedit /etc/X11/xorg.conf
``` did not work and when i put in ```
nvidia-settings
``` it come up with [IMG]http://i17.tinypic.com/7xj2cs1.png[/IMG]

Thanks in advance,

Thomas

---

### Post by Joshua on 2007-12-19
When you say

```
gksudo gedit /etc/X11/xorg.conf
```

didn't work.  Do you mean that gedit didn't open and let you edit that file?  Or do you mean that you made the change, and then restarted (or did <alt>+<ctrl>+<backspace>) and it still didn't let you choose better resolutions?

As far as the nvidia drivers go.  Go to System -> Administration -> Restricted Drivers.  Does that suggest that you install nvidia drivers?

---

### Post by r-mo on 2007-12-19
Please can you post the output of 

```
lspci
```

That will tell us what graphics card you have.  

Are you sure your monitor can cope with a 1280x800 widescreen resolution,  it can sometimes be prudent to include a standard resolution like 1024x768 when you dpkg-reconfigure xserver

---

### Post by ThomasWii on 2007-12-19
i could edit the xorg file, and when i open it now it says vesa and the res is 1280x800, and the only thing in the restricted driver thing is my wireless thing.

---

### Post by ThomasWii on 2007-12-19
r-mo my laptop can handle up to 1280x800, the output is ```
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

```

---

### Post by r-mo on 2007-12-19
Your graphics card is "01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)" so change

```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

```

to 

```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

```

then <ctrl>+<alt>+<backspace> and see if it comes up right

---

### Post by Joshua on 2007-12-19
Keep in mind that every time you change the graphics settings, they won't take effect until you restart that xserver.  To do that you have to reboot, or do <alt>+<ctrl>+<backspace>.  I only keep mentioning it because I change things all the time but then forget to restart.

r-mo is correct, when I select resolutions, I will usually choose the highest that the monitor and graphics card can do, as well as all of those that are below it.

I'm running out of ideas now.  The UniChrome Pro should, I think, either use the sis driver (which you had), or the via driver.  Maybe you can re-run dpkg-reconfigure xserver-xorg and choose the via driver and add the other resolutions.

---

### Post by r-mo on 2007-12-19
There's also the fancy new screens and graphics configuration tool that lives in System->Administration which is supposed to take care of this kinda thing for you.  I can't say I've ever got it to work but I have a strange configuration with dual display on sli twin graphics cards :).

But you now know just what graphics card you have so it should work ok

---

### Post by ThomasWii on 2007-12-19
nope still (unfortunally) dose not work :(

---

### Post by Joshua on 2007-12-19
Can you post your current xorg.conf file again?

---

### Post by ThomasWii on 2007-12-19
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by danwood76 on 2007-12-20
try changing the display driver to vesa as this should work and display the correct resolution. 
So change 
	Driver		"via" 
to
	Driver		"vesa"

Then I would look into re installing the correct graphics driver. as you obviously arent loading the correct driver.

---

### Post by ThomasWii on 2007-12-20
nope still unfortunally dose not work

---

### Post by ThomasWii on 2007-12-21
anybody got any more ideas?

---

### Post by danwood76 on 2007-12-21
yeah, I would try to recompile the driver for your graphics card.
Its not loading as you still get the same results no matter which driver you tell it to use.

regards,
Danny

---

### Post by ThomasWii on 2007-12-21
please note that I'm only 12, could you tun me through this?

---

### Post by danwood76 on 2007-12-21
To be honest I think its a bit strange that the vesa drivers didnt work, as vesa is like a generic driver without excelleration.
Im not sure ho you would go about recompiling the driversfor your board.

You might try re installing gutsy, does the live CD give you correct resolutions?

regards,
Danny

---

### Post by ThomasWii on 2007-12-21
i did not have Gutsy on a live disk, i had feisty (i think that's how you spell it)  then upgraded it.

---

### Post by ThomasWii on 2007-12-21
dose that help?

---

### Post by ThomasWii on 2007-12-21
come on, i don't want to be pushy, but it's nearly christmas and i am getting stuff for this laptop.

---

### Post by ThomasWii on 2007-12-21
look, is there any thing else i can do? or should i give up?

---

### Post by ThomasWii on 2007-12-21
I fiddled with the xorg file

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "un"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Generic Video Card"
    Driver        "vesa"
    BusID        "PCI:1:0:0"
    VideoRam    64000
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x800"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection
```

---

### Post by ThomasWii on 2007-12-21
after a lot of hassle I've got it to work :) thank you for all your help

---

