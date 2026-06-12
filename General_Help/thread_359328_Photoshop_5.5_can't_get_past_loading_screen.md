---
title: "Photoshop 5.5 can't get past loading screen"
date: 2007-02-11
forum: General Help
---

### Post by tylersticka on 2007-02-11
Greetings,

I have successfully installed several apps on my newly-Xubuntu'd laptop machine. I love GIMP, but as a designer I occasionally need access to a true version of Photoshop.

The application installed like a dream, and when I select it from the menu the typical Photoshop splash screen appears promisingly. Unfortunately, it doesn't get past that point and closes entirely.

I ran the application in the terminal so I could see if Wine was publishing any errors, but I can't make heads or tails of it:

```
wine "/home/tylersticka/.wine/c/Program Files/Adobe/Photoshop 5.5/Photoshp.exe"
fixme:palette:GetICMProfileA (0x580, 0x7fb9dea0, 0x7fb9e0a4): partial stub
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9db14,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x7fb9db14,0x00000000), stub!
fixme:mscms:EnumColorProfilesA ( (nil), 0x7fb9dea4, 0x7fb9e4a4, 0x7fb9de9c, 0x7fb9de98 ) stub
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  144 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  264
  Current serial number in output stream:  264

```

I couldn't find this problem referenced anywhere else. If anyone has any suggestions (or even an alternate version of Photoshop they have experience with running smoothly), please volunteer them.

Thanks for your time!

---

### Post by tylersticka on 2007-02-11
Bump. :-)

---

### Post by Shay Stephens on 2007-02-12
A couple of things.  Wine version .9.28 and .29 didn't work for me with PS7.  So use .9.27 or .9.30, they both work for me.  You can check your version in the terminal with 
```
wine --version
```

Another tip that helps me is to launch the app with windows paths like this:
wine "C:\Program Files\Adobe\Photoshop 5.5\Photoshp.exe"

Wine translates that to the actual linux path, but it helps some programs to have the native windows path when it starts.

I hope that helps.

---

### Post by tylersticka on 2007-02-12
Launching with the Windows path didn't help in this situation, but I will remember it.

I was using 9.5, but I changed it to 9.30 using the Package Manager. It took a little longer to crash this time, and I got a longer error message:

```

wine "C:\Program Files\Adobe\Photoshop 5.5\Photoshp.exe"

fixme:rpc:alloc_serverprotoseq protseq "mswmsg" not supported
fixme:palette:GetICMProfileA (0x580, 0x33de58, 0x33e05c): partial stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33dacc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x33dacc,0x00000000), stub!
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
fixme:rpc:I_RpcWindowProc (0x10022,0000001d,00000000,00000000): stub
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  144 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  260
  Current serial number in output stream:  260

```

Any ideas? Should I try 9.27? Is there a painless way to downgrade Wine through the Package Manager or terminal to that version? Or is the problem deeper than that?

Thanks for your help so far!

---

### Post by Shay Stephens on 2007-02-12
Yes, you can uninstall one wine version in synaptic and then download and run an older version of ine if you get the deb file for it.  Just right clickon the deb file, open with gdebi, and install.  You can get older versions here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

As far as the error, I don't know.  Stepping out on a limb and doing abit of searching I ran across someone with a similar error trying to run a game.  They mentioned they had an ATI video card.  What kind of card do you have?  And what driver are you using?

---

### Post by tylersticka on 2007-02-13
I installed 9.27 and I'm getting the same error as with 9.30.

I'm on a Toshiba Portege 4010 notebook computer on loan to me from my company when they found out I could make it run decently with Xubuntu. As I didn't purchase it, I had to look up on Toshiba's support site the specs of it. Here's what I found:

> Graphics/Video

• 12.1" TFT Poly-silicon color LCD; internal display supports up to 16M colors at 1024 x 768 (XGA)

• Trident CyberALADDIN-T graphics controller; 16MB external UMA video memory

• 3D Graphics Accelerator, 4x AGP bus support; 2D Graphics Accelerator, BitBLT hardware, Hardware cursor, Direct Draw support

I must admit I don't have very much experience with hardware and graphics card drivers, so any assistance would be very appreciated.

---

### Post by Shay Stephens on 2007-02-13
Well here is something else you can try.  If you are not using a wacom tablet, you should comment out the mention of it in the xorg.conf file.

```
gksudo gedit /etx/X11/xorg.conf
```

then find the wacom sections and put a # in front of the lines to deactivate it.  It should look similar to this when you are done:
> #Section "InputDevice"
# Driver "wacom"
# Identifier "stylus"
# Option "Device" "/dev/wacom" # Change to
# # /dev/input/event
# # for USB
# Option "Type" "stylus"
# Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection
#
#Section "InputDevice"
# Driver "wacom"
# Identifier "eraser"
# Option "Device" "/dev/wacom" # Change to
# # /dev/input/event
# # for USB
# Option "Type" "eraser"
# Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection
#
#Section "InputDevice"
# Driver "wacom"
# Identifier "cursor"
# Option "Device" "/dev/wacom" # Change to
# # /dev/input/event
# # for USB
# Option "Type" "cursor"
# Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection

then a little further down comment out the input devices
> Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
EndSection

Save the files and close it.  Reboot and then try photoshop again.

---

### Post by tylersticka on 2007-02-13
I commented out the lines described, double-checked to make sure they matched your example, and rebooted. After that, the X server returned errors and wouldn't boot.

I entered the command line through Recovery Mode, navigated to the file and used vi to take out the pound signs and save the file. After I executed a reboot, I was able to get back into Xubuntu normally.

I did some searching and found two pages referencing the installation of Linux on Toshiba Portege 4000, but none on my exact model (4010).

The page [here]("http://www.it.uc3m.es/ptb/toshiba_portege_4000.html") has the following to say about getting graphics working:

> The graphics controller works very well under the trident driver in XFree86 4.1.0.1 with the CyberbladeXPm chipset selected, and 4MB of VideoRam set. I haven't tried other amounts of ram yet, although I know there should be 16MB available.  The chipset is not autodetected, so get a standard XF86Config-4 and modify it. Perhaps "resolved" would be a better adjective than "autodetected". The driver clearly knows it's there but can't decide which chipset to set for it, probably because it's not in its builtin table of PCI ids. You get 1024x768 at 70Hz on the LCD at 75MHz clock. Here's my modeline (56.8KHz hsync):

Section "Monitor"
        Identifier   "LCD"
        VendorName   "Toshiba"
        ModelName    "Portege 4000"
        HorizSync    31.00 -  61.00
        VertRefresh  50.00 -  75.00
        Option       "DPMS"
        Modeline     "1024x768"  75.00   1024 1048 1184 1328    768  771  777  806 -hsync -vsync
EndSection

Of course I just made those hsync/vsync limits up myself, I have no idea what the "right" values are.

In the Screen section of the XF86COnfig-4 file, you want something like:

Section "Screen"
        Identifier "Screen0"
        Device     "CyberBlade XPm"
        Monitor    "LCD"
        DefaultColorDepth 16
        ...
        SubSection "Display"
                Depth     16
                Modes        "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

And in the Device section - the bit that sets up the driver - you want

Section "Device"
        Identifier        "CyberBlade XPm"
        Option            "CyberStretch"
        VideoRam          4096
        Driver            "trident"
        VendorName        "Toshiba"
        BoardName         "CyberBlade XP"
        ChipSet           "cyberbladeXPm"
        #BusId             "PCI:1:0:0"
EndSection

I also got the card working very nicely under the generic vesa driver. For this you need vesa graphic framebuffer support in the kernel (and vesa console framebuffer if you want fun). Then replace "Cyberblade XPm" with "Vesa" in the  Screen section shown above and define the Vesa device driver thusly:

Section "Device"
        Identifier  "Vesa"
        Driver      "vesa"
        Option      "shadowfb"
EndSection 



At this point, I'm considering just to stop trying... GIMP is fine, I just wanted a little bit of native support, but I'm not sure it's actually worth the work!

---

### Post by Soulxlight on 2007-02-13
Yea...you will not be able to load X if you don't make sure to comment out the last three lines related to Input Device stylus, eraser, and cursor. Did you make sure to comment them out when you commented out the wacom lines ?

---

### Post by tylersticka on 2007-02-13
I'm sure I did, especially since I just had to uncomment them in command line.

---

### Post by Shay Stephens on 2007-02-13
Could you post a copy of your xorg.conf.  Maybe there is something else that needs attention once the standard wacom stuff is disabled.  And just to verify, you don't use a wacom tablet do you?

---

### Post by tylersticka on 2007-02-13
I'm a designer, so mine is hooked up to my regular desktop machine 24/7, and I have no intention of hooking the tablet up to this laptop.

Here are the contents of my xorg.conf:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Trident Microsystems CyberBlade XPAi1"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems CyberBlade XPAi1"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Thank you very much for your help so far.

---

### Post by Shay Stephens on 2007-02-13
I edited the your xorg.conf, the changes are in red

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

[COLOR="Red"]#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection[/COLOR]

Section "Device"
	Identifier	"Trident Microsystems CyberBlade XPAi1"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems CyberBlade XPAi1"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
[COLOR="Red"]#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"[/COLOR]
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

If that errors out too, note down the error message, it might point a finger at the problem.

---

### Post by tylersticka on 2007-02-13
I humbly admit my earlier mistake, as this time it booted up just fine.

And guess what?

It works!!

Photoshop boots up perfectly!

Thank you so much for your help, I really really *really* appreciate it.

---

### Post by Shay Stephens on 2007-02-14
Yayyyyyyy!!!!! :) :) :) :)

---

