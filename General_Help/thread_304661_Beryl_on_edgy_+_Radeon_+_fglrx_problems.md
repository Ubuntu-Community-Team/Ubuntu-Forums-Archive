---
title: "Beryl on edgy + Radeon + fglrx problems"
date: 2006-11-22
forum: General Help
---

### Post by mailbinoy on 2006-11-22
Hi guys,

I am having problems running beryl on my onboard ati Radeon card. If i use the radeon driver in my xorg.conf the resolution i get is 800x600 which wont work for me. 
If i install fglrx everything works great, except beryl.
i can login to normal KDE session without problems.
however when i login to my XGL session from kdm, it logins,  and the machine shops responding as soon as some window opens or i right click on desktop. Nothing works, my keyboard stops responding, so i cant even kill X 
i followed the steps at 
[http://www.smorgasbord.net/ati_beryl_kde_dapper_my_guide](http://www.smorgasbord.net/ati_beryl_kde_dapper_my_guide)
which starts X server as
> 
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
exec startkde

Can somebody please help?

---

### Post by Random20230808 on 2006-11-22
At the official Ubuntu documentation I see the following code to start Xgl session on KDE :
> #!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec startkde
See the whole view and you may get an answer :
[https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")

---

### Post by procras on 2006-11-22
In dapper Beryl worked for me with the fglrx supplied.

In edgy I had to install the newer fglrx
[fglrx] module loaded - fglrx 8.31.5 [Nov  9 2006] on minor 0
to get Beryl to work.

I also had to run beryl-manager and berly-xgl 
beryl-manager alone did not work for me.

I have found that the best howtos for beryl are found at
[http://forum.beryl-project.org]("http://forum.beryl-project.org")

Distro: Edgy kernel 2.6.17-10-386
Processor: model name      : AMD Athlon(tm) 64 FX-53 Processor
Motherboard: Abit Av8
Graphics card: X800XT PE  
fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
OpenGL version string: 2.0.6174 (8.31.5)

---

### Post by Random20230808 on 2006-11-23
Did you have any problems with your ATI when installing Beryl?

---

### Post by daradib on 2006-11-23
I did not have any problems.
I used the directions at [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL#Install_XGL_and_Beryl](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL#Install_XGL_and_Beryl)

However, I used different repositories.

---

### Post by strabes on 2006-11-23
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

don't use 3rd party guides. ever.

---

### Post by mailbinoy on 2006-11-29
thanks for all your suggestions guys, but no luck yet.
i reinstalled beryl using the official guide
My KDE starts up with 

Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4
export DISPLAY=:1
exec startkde

but as soon as i right click on the desktop or open a window everything just hangs(beryl-manager has not been started yet)
here is the output from fglrxinfo when i am running the normal kde session (on display 0)

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

i am loading fglrx in /etc/modules
I have ATI Radeon Xpress 200 (RC410) if that matters
my xorg.conf has the following

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon Xpress 200 (RC410)"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:5:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:5:0"
EndSection

---

### Post by Random20230808 on 2006-11-29
Add the following lines in your xorg.conf and try again :
```
Section "Extensions"
        Option "Composite" "Disable"
EndSection

```
This disables the Composite feature on Xgl that ATI does not support.
There is also a tip in Ubuntu tutorial for Xgl installation that says to try > DISPLAY=:0
instead of > DISPLAY=:1 on Edgy, if you experience problems.
Good luck.

---

### Post by mailbinoy on 2006-11-30
> **emsyr said:**
> Add the following lines in your xorg.conf and try again :
```
Section "Extensions"
        Option "Composite" "Disable"
EndSection

```
This disables the Composite feature on Xgl that ATI does not support.
There is also a tip in Ubuntu tutorial for Xgl installation that says to try 
instead of  on Edgy, if you experience problems.
Good luck.

Thanks. I already have the composite disable option in my xorg.conf. 
i tried display=0, its starts kde without problems but when i start berryl-manager (or beryl-xgl) it says
```

XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

```
which i assume means xgl has not started
```

$ps aux | grep X
root      6123  2.4  2.3  28416 21484 tty7     SLs+ 10:40   0:06 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-r1Bx8n
babu      6256  0.0  0.9  27060  8456 ?        S    10:41   0:00 kio_file [kdeinit] file /tmp/ksocket-babu/klauncheraNrFUb.slave-socket /tmp/ksocket-babu/kdesktopoOXREa.slave-socket
babu      6520  0.0  0.0   2804   744 pts/1    S+   10:44   0:00 grep X

```

---

### Post by Blario on 2006-11-30
> **mailbinoy said:**
> Thanks. I already have the composite disable option in my xorg.conf. 
i tried display=0, its starts kde without problems but when i start berryl-manager (or beryl-xgl) it says
```

XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

```

It's that right there that's messing me up.  I'm trying this on a ATI card, so I may have restrictions on me that others don't.  As I understand it, the fglrx driver (8.28) doesn't support DRI while composite is turned on.... and i definitely need DRI for beryl (as far as I understand it).   

I catch HELL everytime I add that composite disable line to xorg.conf .  comp completely locks up and I don't even know how to check any of the logs at that point (they seem to reset once i boot again).  Does anyone else have this problem as well?  Anyone know of a solution?

It's a x200m card and I'm on edgy eft .... uname -r ==> 2.6.17-10-generic

---

### Post by Random20230808 on 2006-11-30
Are you sure that Xgl is running correctly?
After login open a terminal and try :```
ps -e | grep Xgl 
```If your Xgl is running you should have back a result.
If not something is wrong with your Xgl.

---

### Post by Blario on 2006-11-30
> **emsyr said:**
> Are you sure that Xgl is running correctly?
After login open a terminal and try :```
ps -e | grep Xgl 
```If your Xgl is running you should have back a result.
If not something is wrong with your Xgl.

Edgy Eft comes with AIGLX already installed.  I got it working that way on my i386 Nvidia desktop earlier this week.  I'm currently not that far in the process though, I'm still  trying to get DRI up (3D acceleration with proper drivers).  The fglrx driver is actually running, just that I can't turn composite off in xorg.conf without hard crashing the laptop, which seems to be required in order to enable DRI on fglrx.

---

### Post by Blario on 2006-11-30
[http://gentoo-wiki.com/HOWTO_ATI_Drivers#DRI_problems_with_ATI_XPRESS_200M_PCIe](http://gentoo-wiki.com/HOWTO_ATI_Drivers#DRI_problems_with_ATI_XPRESS_200M_PCIe)

That describes my situation exactly, specific to the GPU & make&model of the comp.  I'm looking more into it.

---

### Post by Random20230808 on 2006-11-30
OK. But don't forget you're using the Ubuntu distribution and not the Gentoo one. That means that thinks may work a slight differently.... That is an important issue to deal with...

---

### Post by daradib on 2006-11-30
> It's that right there that's messing me up. I'm trying this on a ATI card, so I may have restrictions on me that others don't. As I understand it, the fglrx driver (8.2 doesn't support DRI while composite is turned on.... and i definitely need DRI for beryl (as far as I understand it). 

It can't be only the graphics card. I am using an ATI Radeon X800 PCI-E on Kubuntu Edgy Eft 64-bit and XGL/Beryl works fine.

This URL worked for me:
[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL)
You could try using that.

---

### Post by daradib on 2006-11-30
Never mind. Disregard this message.

---

### Post by 89camarorsv6 on 2006-12-02
> **Blario said:**
> It's that right there that's messing me up.  I'm trying this on a ATI card, so I may have restrictions on me that others don't.  As I understand it, the fglrx driver (8.28) doesn't support DRI while composite is turned on.... and i definitely need DRI for beryl (as far as I understand it).   

I catch HELL everytime I add that composite disable line to xorg.conf .  comp completely locks up and I don't even know how to check any of the logs at that point (they seem to reset once i boot again).  Does anyone else have this problem as well?  Anyone know of a solution?

It's a x200m card and I'm on edgy eft .... uname -r ==> 2.6.17-10-generic

I also seem to have the same problem with teh same video card on a laptop X200 , with the same config I use the XGL.desktop as a session as described and have tried multiple methods of launching Xgl. It basically hard locks the system.  I have also tried sshing in from another system and watch "top" output while logging in as Xgl desktop. Nothing looks wierd Xgl runs normally on top and suddenly it hangs.

I am wondering if I can use AIGLX on this ATI Card. I have a desktop running gentoo with Xorg7.1 with AIGLX working perfectly on an NVIDIA 7900GT with Nvidia Beta Drivers. I wish there was something I could do in ubuntu.

---

### Post by 89camarorsv6 on 2006-12-02
Also one other thing. I had this entire thing working( Xorg 7+ XGL + Beryl 0.1 + FGLRX) when I was using Dapper, I upgraded to Edgy and this thing still worked for a couple of times, before it started hard locking on me.

Makes me wonder if its XGL / Beryl (both of which I have tried manually downgrading / upgrading to various versions).

---

### Post by Blario on 2006-12-03
> **89camarorsv6 said:**
> Also one other thing. I had this entire thing working( Xorg 7+ XGL + Beryl 0.1 + FGLRX) when I was using Dapper, I upgraded to Edgy and this thing still worked for a couple of times, before it started hard locking on me.

Makes me wonder if its XGL / Beryl (both of which I have tried manually downgrading / upgrading to various versions).

Now that is weird that you say you had it working before, because I think I found out what my issue is/was.  With that added detail though, I can't say that this fits for you....

[http://gentoo-wiki.com/HOWTO_ATI_Drivers#DRI_problems_with_ATI_XPRESS_200M_PCIe](http://gentoo-wiki.com/HOWTO_ATI_Drivers#DRI_problems_with_ATI_XPRESS_200M_PCIe)
reads (as of today)....
```

**DRI problems with ATI XPRESS 200M PCIe**

_Issue with DRI; Compaq Presario R4000 Series (R4146EA) and HP Pavilion dv5000 and zv6000 with ATI XPRESS 200M PCIe_

These laptops both appear to have the same problem:

On startup, the X process hangs with a blank screen, using 99%, however SSH access is possible. The "NoDRI" option in xorg.conf prevents the lockup, but has its obvious drawbacks. Rolando Zappacosta originally reported that lspci -v was incorrectly reporting the video memory size regardless of the actual value configured in the system BIOS, however this was not the case on the dv5000.

EDIT: The driver does work on my compaq v2000 series with the ATI XPRESS 200M

Workaround:

In the system BIOS the "SidePort+UMA" option must be selected, and an additional 128M of system memory must be assigned to the VGA. It is unknown whether this is a bug in the HP's BIOS, in the Linux PCI code, or the fglrx driver. 

```

The workaround didn't work for me, and I forget what the reason for that is, but as you can see, it's a specific problem with an even more specific make and combination of hardware.  Really sux that I fit into this criteria.

---

### Post by 89camarorsv6 on 2006-12-03
Blario,

Thanks for the reply, I cant seem to find that bios option "SidePort+UMA" my laptop is a presario M2200 with the AMD Sempron 2800+ with ATI mobility X200 M. Do I have to do a bios update or something?.

```

01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

```

As you can see glx accel is on and working.
```


$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

This is driving me crazy to the point that I want to reinstall dapper and get beryl working the way it was.

This was my timeline.

1. Dapper <- Beryl worked flawlessly (0.1) but couldnt play any games. (with XGL)
2. Upgrade to Edgy <- Beryl 0.1.2 worked fine a couple of times. (with XGL)
   (I was having some artifacting when I was opening a terminal or something else from the panel bar..figured this was because of enable animations in the panel in gconf editor)
3. Now if I Login to Xgl Session and everything seems to be ok until XGL loads fully and beyrl loads and first movement of hte mouse hangs the system.

---

### Post by Blario on 2006-12-03
> **89camarorsv6 said:**
> Blario,

Thanks for the reply, I cant seem to find that bios option "SidePort+UMA" my laptop is a presario M2200 with the AMD Sempron 2800+ with ATI mobility X200 M. Do I have to do a bios update or something?.

I didn't have to do one, but perhaps you do.  On mine, it's the last or second to last tab, and it's an option about your video card.  It should be already be set to sideport (meaning RAM is on board the card), and you switch it to "Sideport+UMA" to mean on-board-RAM & shared system RAM.  Then you add how much you'd like to add to the 128MB detected (an addition 128MB).

It didn't work for me, I believe cause I'm trying version 8.28 of the driver.  I probably won't worry about it anymore until I see that there's a working solution to the problem online.

> **89camarorsv6 said:**
> 
As you can see glx accel is on and working.
```


$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

That may not mean that it's working.  You should see a line saying DRI: enabled that indicates that your composite is disabled and DRI therefore loaded correctly.  Perhaps check that you have composite disabled in your xorg.conf file.

---

### Post by 89camarorsv6 on 2006-12-04
DRI is enabled and compositing is disabled

I am right now doing all this (Note I added those to see if those were the problem

```

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        BusID       "PCI:1:5:0"
   Option       "no_dri" "no"
   Option       "DynamicClocks" "on"
   Option       "mtrr" "off"
   Option       "DesktopSetup" "Single"
   Option       "ScreenOverlap" "0"
   Option       "Capabilities" "0x00000000"
   Option       "CapabilitiesEx" "0x00000000"
   Option       "VideoOverlay" "on"
   Option       "OpenGLOverlay" "off"
   Option       "CenterMode" "off"
   Option       "PseudoColorVisuals" "off"
   Option       "Stereo" "off"
   Option       "StereoSyncEnable" "1"
   Option       "FSAAEnable" "no"
   Option       "FSAAScale" "1"
   Option       "FSAADisableGamma" "no"
   Option       "FSAACustomizeMSPos" "no"
   Option       "FSAAMSPosX0" "0.000000"
   Option       "FSAAMSPosY0" "0.000000"
   Option       "FSAAMSPosX1" "0.000000"
   Option       "FSAAMSPosY1" "0.000000"
   Option       "FSAAMSPosX2" "0.000000"
   Option       "FSAAMSPosY2" "0.000000"
   Option       "FSAAMSPosX3" "0.000000"
   Option       "FSAAMSPosY3" "0.000000"
   Option       "FSAAMSPosX4" "0.000000"
   Option       "FSAAMSPosY4" "0.000000"
   Option       "FSAAMSPosX5" "0.000000"
   Option       "FSAAMSPosY5" "0.000000"
   Option       "UseFastTLS" "0"
   Option       "BlockSignalsOnLock" "on"
   Option       "UseInternalAGPGART" "no"
   Option       "ForceGenericCPU" "no"
   Option       "KernelModuleParm" "agplock=0"
   Option       "PowerState" "1"
EndSection


```


```


Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

```

---

### Post by 89camarorsv6 on 2006-12-04
On the bios side all I have is Video Memory -> which is now at 128M

Also Xgl Starts with the following options in /usr/bin/startxgl

```

#!/bin/sh

Xgl -softcursor -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & 
DISPLAY=:1 
exec gnome-session


```

I have also tried this instead of the exec gnome-session

exec dbus-launch --exit-with-session gnome-session

---

### Post by 89camarorsv6 on 2006-12-04
Made some more progress today, On a regular gnome session I started Xgl manually on :1 and it didnt hang , then I started beryl & emerald on :1 it still didnt hang, When I tried to start emacs it froze.

This one is driving me insane to the point that I am thinking of reinstalling dapper.

Is there a way to get beryl 0.1.1 on edgy?.

---

### Post by spednik on 2006-12-04
> **Blario said:**
> It's that right there that's messing me up.  I'm trying this on a ATI card, so I may have restrictions on me that others don't.  As I understand it, the fglrx driver (8.28) doesn't support DRI while composite is turned on.... and i definitely need DRI for beryl (as far as I understand it).   

I catch HELL everytime I add that composite disable line to xorg.conf .  comp completely locks up and I don't even know how to check any of the logs at that point (they seem to reset once i boot again).  Does anyone else have this problem as well?  Anyone know of a solution?

It's a x200m card and I'm on edgy eft .... uname -r ==> 2.6.17-10-generic

I am in literally the exact same situation, same card, and everything. 
I am able to get direct rendering, the 3d is working fine on my xpress 200 card with the fglrx, installed xgl, beryl, ext, but get the exact same message when running "beryl" in terminal 
I tried running ps -e | grep Xgl and it gave me no return, so I guess that would have something to do with it...but xgl is installed! frustrating...

---

### Post by Blario on 2006-12-05
> **89camarorsv6 said:**
> 
Is there a way to get beryl 0.1.1 on edgy?.

Even from [http://beryl-project.org](http://beryl-project.org) , it seems like they only distribute the source in the most recent trunk form...  You would have to get it from someone that has saved already or something.  I'm just curious, when you run 'lspci', what are the numbers (chipset) that it says after the name of your video card?  Mine is chipset 5955 and won't even open start X with DRI enabled.  I have yet to try all the different versions of the driver that are available out there yet.  (no time)
> lspci | grep "ati"
or
> lspci | grep "ATI" 
... in order to see the line.

> **spednik said:**
> 
I am in literally the exact same situation, same card, and everything.
I am able to get direct rendering, the 3d is working fine on my xpress 200 card with the fglrx, installed xgl, beryl, ext, but get the exact same message when running "beryl" in terminal
I tried running ps -e | grep Xgl and it gave me no return, so I guess that would have something to do with it...but xgl is installed! frustrating...

Strange. If you actually have DRI enabled, (fglrxinfo does not say that it's disabled), than I'm not even that far, and can't say I know what the problem is.  I refuse to try XGL so far, seeing that beryl should work on Edgy Eft without it [AIGLX!!] (like it is on my desktop).  

If you did not disable composite in xorg.conf and you're using the fglrx driver, with the 200m card, than DRI would be disabled... the driver doesn't support both at the same time.

---

### Post by spednik on 2006-12-05
I'm seriously confused...heres my current situation, if anyone could help me...

spednik@zippy:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

seems to be normal...glxgears works fine 

heres this 
spednik@zippy:~$ glxinfo | grep direct
direct rendering: Yes

heres my xorg.conf 
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
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"VA702b"
	Option		"DPMS"
        HorizSync       30-82
        VertRefresh     50-85 

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
	Monitor		"VA702b"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection  

I'm a little confused....heres what happends when i run beryl 
spednik@zippy:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension


I do have xgl installed.......what should i do about this?

---

### Post by 89camarorsv6 on 2006-12-06
spednik,

couple of things.

1. Do you have Xgl running from startxgl.sh on :1 using a seperate GDM entry?
2. try 

# beryl-xgl 

3. try 

# ps xa | grep Xgl 

and see if xgl is running

---

### Post by spednik on 2006-12-06
Yeah I have a a startxgl.sh...when I log in using it everything fuzzes out...blurs everything all up..the splash screen greys out, all sorts of problems. 

beryl-xgl  sent me into some sort of grey death type screen...cursor turned into an X...it was nasty

and heres this.. not sure the meaning of it 
spednik@zippy:~$ ps xa | grep Xgl 
 5080 pts/0    R+     0:00 grep Xgl

---

### Post by Random20230808 on 2006-12-07
Also try```
ps -e | grep Xgl
```
to see if Xgl is running.

---

### Post by 89camarorsv6 on 2006-12-08
I got some more news on this topic.

1. I did a completely new reinstall of Edgy from CD.
2. Installed linux-restricted-modules for fglrx
3. Installed XserverXGL
4. Installed Beryl from Trevino's repository for unstable 0.1.3

Eveyrthing worked like a charm till I installed gtk2-engines-pixbuf and rebooted.

Now its back to the hanging thing again. I log into Xgl session and it hangs / hard locks. I can still login to regular gnome and get fglrxinfo , etc.

I am going to reinstall one more time leave it at step 4, and reboot a couple of times. I have a feeling something else goes on..with the fglrx driver

---

### Post by Xemanth on 2006-12-18
I have now working Xgl + KDE + Beryl

Beryl effects are working great but now I have problem:
Any idea what causes those error messages. I can launch ioquake3 but textures are all cra*.

xemanth@5024wlmi:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.6234 (8.32.5)

xemanth@5024wlmi:~$ glxinfo 
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No

xemanth@5024wlmi:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Error: couldn't get fbconfig
xemanth@5024wlmi:~$
--------------------------------------------------
In xorg.conf I have these:
Section "Extensions"
        Option      "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

and in device section:
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"

        Option     "XaaNoOffscreenPixmaps"

---

### Post by Random20230808 on 2006-12-18
Have you checked that your "fglrx" driver works correctly?
Read [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") to see how to check it.

---

### Post by Xemanth on 2006-12-18
> **emsyr said:**
> Have you checked that your "fglrx" driver works correctly?
Read [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") to see how to check it.

Yeah, my Xorg works fine with direct rendering IF I don't use Xgl.
I wonder what causes my problem... well I know what causes it: ati.

---

### Post by daradib on 2006-12-18
Yeah, I have the same problem. Driver works perfectly when not using XGL. When I use XGL, I lose my direct rendering support and cannot play games with OpenGL.

Kubuntu 6.10 64-bit
ATI Radeon X800 PCI-E with fglrx drivers
AMD Athlon64

---

### Post by Blario on 2006-12-18
This ATI crap is horrible.  I may never get beryl working on my laptop....  My desktop (FX 5200) has become an old favorite reborn since attempting beryl.  I hope they lose some *good* marketshare over this crap! (lol... linux users effecting marketshare)

---

### Post by Xemanth on 2006-12-19
Btw how do I make my shift work like shift again, with Xgl and beryl shift + backspace restarts Xgl or something... Its really annoying....I accidentally hit it all the time. Mainly when when writing something important.

---

### Post by pormogo on 2006-12-19
Yeah shift+backspace still crashes Xgl major bummer =( there is an xmodmap fix out there. I'm still trying to get the whole driver situation totally straight here. I have heard a few different versions of the story and here they all are laid before you.

-The current apt-get able version of fglrx from the ubuuntu repos does not support compositing and therefore does not support aiglx. 
-The current apt-get able version of fglrx does not support DRI while compositing is turned on so you can use aiglx and fglrx but only without DRI which kinda eliminates the point. 
-The current apt-get able version of fglrx from the ubunutu repos doesn't suppport aiglx at all however the newer version off of the ati website does (I have not verified this myself)
-All versions of fglrx under the sun are cursed and from hell itself and do not support aiglx at all, for now you must use the "radeon" driver and pray for an update.

Could someone please clarify which of these statements is true. I have no issue getting fglrx (binary) running however the "radeon" driver won't give me DRI support to save my life. I just wanted to know if it would be possible to just disable DRI in fglrx and use compositing instead.

---

### Post by daradib on 2006-12-23
Ignore this post. Sorry, there were duplicate posts.

---

### Post by daradib on 2006-12-23
> Could someone please clarify which of these statements is true. I have no issue getting fglrx (binary) running however the "radeon" driver won't give me DRI support to save my life. I just wanted to know if it would be possible to just disable DRI in fglrx and use compositing instead.
As far as I know:
Statement 1 is true if DRI is required- > The current apt-get able version of fglrx from the ubuuntu repos does not support compositing and therefore does not support aiglx.
For statement 2- I believe aiglx requires both composite extensions and DRI, which you can't do with the fglrx drivers. You can have composite extensions only or DRI only, but not both at the same time- > The current apt-get able version of fglrx does not support DRI while compositing is turned on so you can use aiglx and fglrx but only without DRI which kinda eliminates the point.
I'm not sure about Statement 3- I don't really know- > The current apt-get able version of fglrx from the ubunutu repos doesn't suppport aiglx at all however the newer version off of the ati website does (I have not verified this myself)
I believe that by leaving compositing extensions at default status (enabled), you will not get DRI. By disabling composite extensions, you will get DRI with the fglrx drivers. At least that's how it was with my computer and graphics card.
Correct me if I am wrong.
Lesson learned: fglrx drivers stink. If you have an ATI Radeon card like me, then your graphics card and its driver will be the weak link in GNU/Linux distributions including Ubuntu.

---

### Post by Blario on 2006-12-23
> **daradib said:**
> As far as I know:
Statement 1 is true if DRI is required- 
fglrx can't do both at the same time, plus Beryl && the rest of these XGL derivatives require direct rendering.  I think that would be a false (for all utilsive purposes.
> **daradib said:**
> 
For statement 2- I believe aiglx requires both composite extensions and DRI, which you can't do with the fglrx drivers. You can have composite extensions only or DRI only, but not both at the same time- 
Correct.  Therefore, when trying all this with fglrx drivers, you have to use XGL as well (not aiglx) (as far as I know it).
> **daradib said:**
> 
I'm not sure about Statement 3- I don't really know- 
I think he's basically right.... It would eliminate the point, even if it is possible, so it doesn't pay to think much more about it.
> **daradib said:**
> 
I believe that by leaving compositing extensions at default status (enabled), you will not get DRI. By dsiabling composite extensions, you will get DRI with the fglrx drivers. At least that's how it was with my computer and graphics card.
Correct me if I am wrong.
Lesson learned: fglrx drivers stink. If you have an ATI Radeon card like me, then your graphics card and its driver will be the weak link in GNU/Linux distributions including Ubuntu.
Well stated!  Exactly where I'm at... especially since I have this horrid x200m & hp mobo combination....  And yes, that's the way it worked for me also.  enable one... the other doesn't load.  basically does not do both at the same time, which it even stated on some site that i read.  So right, it doesn't support aiglx.  Concerning a newer version of fglrx.... i don't know anything about that.  i'm kinda waiting for someone to verify it for me... i'm enjoying beryl 0.1.4 on my desktop, gdesklets, & kiba-dock... and the lappie has kinda fell to the way-side....

---

### Post by Blario on 2007-02-23
> **Blario said:**
> I didn't have to do one, but perhaps you do.  On mine, it's the last or second to last tab, and it's an option about your video card.  It should be already be set to sideport (meaning RAM is on board the card), and you switch it to "Sideport+UMA" to mean on-board-RAM & shared system RAM.  Then you add how much you'd like to add to the 128MB detected (an addition 128MB).

It didn't work for me, I believe cause I'm trying version 8.28 of the driver.  I probably won't worry about it anymore until I see that there's a working solution to the problem online.


That may not mean that it's working.  You should see a line saying DRI: enabled that indicates that your composite is disabled and DRI therefore loaded correctly.  Perhaps check that you have composite disabled in your xorg.conf file.

OMFG IT WORKS!!! IT WORKS!!!! Drivers 8.34.8 actually enable and boot DRI properly for me.  Quite Quite happy about this, as I've been waiting for sooo long....

```
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

```
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

```
Onwards I move towards installing XGL & Beryl....

---

