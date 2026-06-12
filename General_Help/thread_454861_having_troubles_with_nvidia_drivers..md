---
title: "having troubles with nvidia drivers."
date: 2007-05-25
forum: General Help
---

### Post by powerplayground on 2007-05-25
I went to system>administration>Restricted drivers manager and enabled my nvidia driver. When i did this it switched to my secondary display instead of my primary one. I have dual monitors and this has happened to me in xp before i updated to the latest drivers. I went to their site, and there was linux x86, x64, Free BSD, and Solaris. None of them seem to open by themselves. Any Ideas on how to get the latest nvidia driver? 

Also how would i set up my computer to use dual monitors? Not mirored, but 2 independant displays.

---

### Post by kolanos on 2007-05-26
> **powerplayground said:**
> I went to system>administration>Restricted drivers manager and enabled my nvidia driver. When i did this it switched to my secondary display instead of my primary one. I have dual monitors and this has happened to me in xp before i updated to the latest drivers. I went to their site, and there was linux x86, x64, Free BSD, and Solaris. None of them seem to open by themselves. Any Ideas on how to get the latest nvidia driver? 

Also how would i set up my computer to use dual monitors? Not mirored, but 2 independant displays.
Use the nvidia driver provided by the restricted driver tool in Ubuntu (uninstall and reinstall the driver if needed).

Then check here for information on how to setup TwinView:
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

It's a guide for Gentoo, but it will work with Ubuntu as well. Scroll down to the part about TwinView. You're going to need to edit your /etc/X11/xorg.conf file and add TwinView parameters under the Device section.

---

### Post by powerplayground on 2007-05-26
i uninstalled / reinstalled the driver a bunch of times but it still goes to my secondary monitor. Im gonna try out the secondary monitor thing now. Will this let me choose which monitor to use as my secondary and primary? 

Also the driver i have now on linux is a buggy one which causes my vidoe card (nvidida 7900gs to use its secondary monitor as its primary one. this is not a problem without the driver, and on xp i gotthe latest driver and it works fine.

---

### Post by powerplayground on 2007-05-26
any ideas on where to get the most up to date driver for my gfx card?

---

### Post by orb9220 on 2007-05-26
9755 is the latest for nvidia. It may help not sure since I am still learning,

> Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"TwinView" "on"
        Option          "NvAGP" "3"
	Option		"MetaModes" "1280x1024,1280x1024; 1280x1024,NULL; 1024x768,1024x768; 1024x768,NULL"
	Option		"SecondMonitorHorizSync" "30-70"
	Option		"SecondMonitorVertRefresh" "60"
	**Option		"TwinViewOrientation" "RightOf"**		
	Option		"ConnectedMonitor" "CRT,CRT"
	Option 		"AllowGLXWithComposite" "true"
	Option		"RenderAccel" "true"
EndSection

Might yours say Right Of and try changing to Left of?
Just guessing but may work for you.

---

