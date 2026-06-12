---
title: "Laptop not booting when charger plugged in"
date: 2013-08-27
forum: General Help
---

### Post by Suraj_Jungade on 2013-08-27
I have lenovo ideapad z585, which came pre-installed EFI Windows 8, and i've installed ubuntu too in efi mode and everything was fine till i install radeon drivers.

Once i've installed radeon drivers from amd's web site, my ubuntu boots and stucks at purple screen.

If i boot ubuntu when Charger plugged in then everything works fine.

---

### Post by tgalati4 on 2013-08-27
Perhaps the radeon drivers draw too much power from the battery causing an instant freeze.  When plugged in, there is extra power to run the GPU and boot normally.  That is a strange problem.  Are there GPU settings such as Dynamic Clocks that allow the GPU to throttle speed based on workload?  In /etc/X11/xorg.conf:

(I'm using the open source ati driver.)


Section "Device"
	Identifier	"Configured Video Device"
	Driver "ati"
	Option "DynamicClocks" "on"
	Option "mtrr" "on"
	Option "DesktopSetup" "Single"
	Option "ScreenOverlap" "0"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
	Option "Stereo" "off"
	Option "StereoSyncEnable" "1"
	Option "FSAAEnable" "no"
	Option "FSAAScale" "1"
	Option "FSAADisableGamma" "no"
	Option "FSAACustomizeMSPos" "no"
	Option "UseFastTLS" "0"
	Option "BlockSignalsOnLock" "on"
	Option "XAANoOffscreenPixmaps"
	Option "AccelMethod" "XAA"
	#        Option "AccelDFS"    "true"
EndSection

---

### Post by Suraj_Jungade on 2013-08-27
Thanks for very fast reply...
I am not a linux developer, so might be my post like a noob....

I don't think battery might be dead, because it is very new laptop not even 1 month have crossed. And if battery might be issue then laptop should have turned off, but it stays on and as soon i plug in charger it continues the boot (I don't even need to restart)...

Shall i report it as a bug?
Do you need any more info?


More details:
OS: Ubuntu 13.04 64 bit
And I've already updated all the packages

Below is my /etc/X11/xorg.conf file...
[INDENT]

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    BusID       "PCI:0:1:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    Monitor    "aticonfig-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
[/INDENT]

---

### Post by tgalati4 on 2013-08-27
I presume that it works OK in Windows 8 on battery and when plugged in?  As I recall, Win8 doesn't really shut off, but goes into a low-power suspend mode--similar to sleep.  Perhaps the BIOS is doing something similar, but Ubuntu doesn't know how to handle it.  There is *acpitool* that you can use to leave parts of the bus powered during sleep.

So:  Boot Ubuntu with the power cord.  Put it to sleep.  Remove the cord.  Does the tablet come back to life?  If so, then perhaps the BIOS will only let you boot with a power cord, so that it has plenty of power for a complete boot.  After booting, you simply put it to sleep.  You might only need to reboot once every 3 months.  

Of course, this is a pain if you have to dual boot.

---

