---
title: "XGL working but use Mesa drivers"
date: 2008-05-25
forum: General Help
---

### Post by xMaximex on 2008-05-25
I finally get XGL to work on my laptop but when it's activated it uses Mesa Driver instead of ATI's

$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)

$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

I tried with the driver from ATI and the one from Ubuntu repos...

Any help would be appreciated

---

### Post by Forlong on 2008-05-25
You do not need Xgl with that version of the fglrx driver.
Just remove it:
```
sudo apt-get remove xserver-xgl
```

---

### Post by xMaximex on 2008-05-25
I tried to disable xserver-xgl but I can't get compiz to work. I get a blank screen and I must run metacity --replace to see my desktop

---

### Post by Forlong on 2008-05-25
Did you reboot in the meantime?
What's the output of ```
fglrxinfo
``` afterwards?

---

### Post by pietjanjaap on 2008-05-25
This is the last thing i tried:
/etc/modprobe.d/blacklist
Copie these 2 line in above file:

blacklist i82875p_edac
blacklist edac_mc

after this i got compiz working.

This is my xorg:

Section "Device"
	Identifier	"Configured Video Device"
 	Driver		"fglrx"
        Option		"DRI"			"true"
        Option		"ColorTiling"		"on"
        Option		"EnablePageFlip"	"true"
        Option		"AccelMethod" 		"EXA"
        Option		"XAANoOffscreenPixmaps"

Befor this all i tried this:
Setup Compiz Fusion with open source ati radeon drivers

Older ATI cards have been blacklisted for Compiz Fusion because of a bug in the driver, but there is an easy workaround for many cards that use the open source ati drivers. Radeon 9500 are the oldest cards to support the restricted "fglrx" drivers, so everything older requires the open source drivers to function properly.



First edit the launcher for Compiz Fusion:

gksudo gedit /usr/bin/compiz

Near the top, add the line

SKIP_CHECKS="yes"

I added it under VERBOSE="yes"

You may also need to install the Compiz settings manager program that you can access from System->Preferences->Advanced Desktop Effect Settings | 1-click install or:

sudo apt-get install compizconfig-settings-manager

You can now load Compiz Fusion with

compiz --replace

and revert to Metacity (the basic window manager) with

metacity --replace

I suggest making launchers in a panel for this.

Remember that this is a workaround and may not work for everybody. If you have further problems, you should consider running a forum search and then posting on one of the main support forums if you still need help.
For the record, my card is an ATI Mobility Radeon 9000.


Hope this helps you.
Drivers i installed with envy, this is also the last thing you should do,
first change the blacklist file and then skip yes, then install with envy.

---

### Post by xMaximex on 2008-05-25
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

But when I log on I only get a blank screen. To fix this I have to run (ALT+F2) metacity --replace and I get my desktop back.

Here's the output of compiz --replace if I run it in a gnome-terminal:

$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
01:05.0 0300: 1002:5955 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (cubecaps) - Warn: Failed to load image: /media/data/My Documents/My Wallpapers/halo3-1.jpg
/usr/bin/compiz.real (cubecaps) - Warn: Failed to load image: /media/data/My Documents/My Wallpapers/halo3-2.jpg
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

---

### Post by Forlong on 2008-05-25
Do you get the blank screen only on login or every time when trying to run Compiz?

---

### Post by xMaximex on 2008-05-25
Every time I run compiz.

If I run compiz --replace after metacity --replace, I get the blank screen

I can move the mouse and click on buttons and icons (if I know where they are) but I can't see anything so I press ALT+F2 and type metacity --replace without seeing anything

---

### Post by Forlong on 2008-05-25
OK... I'm sorry, I'm not a driver guru but that is a pretty common problem. A quick search on the forums should give you lots of threads -- and hopefully a solution.

---

