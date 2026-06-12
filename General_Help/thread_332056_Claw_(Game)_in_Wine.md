---
title: "Claw (Game) in Wine"
date: 2007-01-05
forum: General Help
---

### Post by theaverageidiot on 2007-01-05
I'm trying to get an old game from '97 to work in Ubuntu. According to WineHQ it's compatible. The game is called Captain Claw. It installed perfectly but here's the error when I try to run it:

```
sudo wine '/home/theaverageidiot/.wine/drive_c/games/claw/CLAW.EXE'
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x170820) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x170110)->(0x10024,00000011)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x170110)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
```

The screen goes black for about a half a second then an error message with the Claw logo says "Unable to load the resource file".

Any ideas?

---

### Post by majoridiot on 2007-01-05
looks like it's failing to init 8 bit color depth for the screen.  make sure your "Screen" section of
xorg.conf has an entry for 8 bit color.  it would look something like this:

```
SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection

```

i'm guessing that 800x600 and 640x40 resolutions for Modes would be sufficient for this game.

---

### Post by theaverageidiot on 2007-01-05
> **majoridiot said:**
> looks like it's failing to init 8 bit color depth for the screen.  make sure your "Screen" section of
xorg.conf has an entry for 8 bit color.  it would look something like this:

```
SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection

```

i'm guessing that 800x600 and 640x40 resolutions for Modes would be sufficient for this game.

Near the bottom of my /etc/X11/xorg.conf is this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
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
```
What do I?

---

### Post by theaverageidiot on 2007-01-05
I changed that one part to this:

```
SubSection "Display"
		Depth		8
		Modes		"1920x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
```

Then logged out and pressed Ctrl + Alt + Backspace to restart Xorg then logged back in. Ran Claw and I get the same error about resource file and this is what terminal says:

```
sudo wine '/home/theaverageidiot/.wine/drive_c/games/claw/CLAW.EXE'
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x170820) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x170110)->(0x10024,00000011)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x170110)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
```

---

### Post by justin whitaker on 2007-01-05
Are you using the vesa drivers, or is 3D DRI enabled? By the looks of that error message, WINE is calling out for something to hook D3D to, and not being able to do it.

---

### Post by theaverageidiot on 2007-01-05
> **justin whitaker said:**
> Are you using the vesa drivers, or is 3D DRI enabled? By the looks of that error message, WINE is calling out for something to hook D3D to, and not being able to do it.
I have NO idea what either of those things are. (Vesa, 3D DRI)

---

### Post by justin whitaker on 2007-01-05
> **theaverageidiot said:**
> I have NO idea what either of those things are. (Vesa, 3D DRI)

By default, Ubuntu will not install 3D support. It installs a basic drive that allows the system to display, but you need to configure the system to handle DRI, or direct rendering.

Check this thread here:

[http://www.ubuntuforums.org/showthread.php?t=221320](http://www.ubuntuforums.org/showthread.php?t=221320)

And the wiki here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).

Take a deep breath: this is not hard, it just has a bunch of steps.

---

### Post by theaverageidiot on 2007-01-05
During the tutorial at this:

```
bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/edgy
```
Of course I replaced <version> with the version on my computer.

I get this:

```
sudo '/home/theaverageidiot/Desktop/here/ati-driver-installer-8.32.5-x86.x86_64.run'
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.32.5........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Unknown X Window
cp: cannot stat `x710/usr/X11R6/bin/*': No such file or directory
find: install/usr/bin/fireglcontrolpanel: No such file or directory
Removing temporary directory: fglrx-install
theaverageidiot@theidiots-computer:~/Desktop/here$ sudo bash ./ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.32.5........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
./packages/Ubuntu/ati-packager.sh: line 56: dpkg-architecture: command not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install
```

---

### Post by majoridiot on 2007-01-06
[redacted]

---

### Post by theaverageidiot on 2007-01-06
> **majoridiot said:**
> [redacted]
Bump

---

### Post by theaverageidiot on 2007-01-06
Puh-leese help me :) (bump)

[EDIT: I got past that error. I didn't have the right repositories or something but I fixed it. I have a few more steps left though. I'll post back soon.]

---

### Post by theaverageidiot on 2007-01-06
Okies, I followed that guide about ATI drivers and finally got through it and now here's what I get:

```
sudo wine '/home/theaverageidiot/.wine/drive_c/games/claw/CLAW.EXE'
Password:
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x170780) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x170070)->(0x10024,00000011)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x170070)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
```

:( Now what?

---

### Post by theaverageidiot on 2007-01-07
HELP me :/ :)?

---

### Post by theaverageidiot on 2007-01-08
Bump yet again

---

### Post by majoridiot on 2007-01-08
> **theaverageidiot said:**
> 
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x170780) : stub, simulating 64MB for now, returning 64MB left

"stub" means that the function it is calling is not yet implemented, in this case it looks like a
call to get the available memory for a texture map.  after that, it appears that it is still failing
to switch to 8 bit color depth from 32.  all of the reported errors seem to be with directdraw
functions.

you might try starting a new X session @ 800x600, 8 bit color to see if anything different
happens...

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.newbak
```

(for safety's sake...) then replace the entire Screen definition with:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor		"Generic Monitor"
	DefaultDepth	8
	SubSection "Display"
		Depth		8
		Modes		"800x600"
	EndSubSection
EndSection
```

restart X (ctrl-alt-bkspace) or reboot to try it out and see what errors you get.  it might be
worth it to also try starting in 640x480 to see if that makes a difference, too.

you can revert back to your original setup with:

```
sudo mv /etc/X11/xorg.newbak /etc/X11/xorg.conf
```

this may or may not relieve the errors... you might just need to wait until the DD wine
implementations are a bit more robust.

btw, what version of wine are you running?  there was a new update a week or so ago.

---

