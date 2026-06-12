---
title: "Activing extra 3d effects all windows disappear o_O"
date: 2008-05-25
forum: General Help
---

### Post by dsom on 2008-05-25
Hi all,
i got Ubuntu 8.04, everything is updated.
My graphic card is an ati radeon 1600 agp 512mb.
I use latest driver from ati that means.. 5.5 ? (from ati site i downloaded ati-driver-installer-8-5-x86.x86_64.run).
i do not use xgl.

that's my problem: if i try to active extra 3deffects all windows disappear, simply become "invisible" but is like they exists (if i guess where they are i can grab them or resize). 
so i'm forced to press "esc" and return to normal screen.

if i try compiz --replace same stuff (just my wallpaper and invisible window), kill compiz and then, all windows come back, but they miss windows-decoration.

now some tech info:

**fglrxinfo **
```
dsom@Metropolis:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.1.7537 Release

```

Utility Compiz-check sign everything ok.

**Compiz stuff installed: **
```

dpkg -l | grep compiz
ii  compiz                                                                       
ii  compiz-core                                                                  
ii  compiz-fusion-plugins-extra                                                  
ii  compiz-fusion-plugins-main
ii  compiz-gnome
ii  compiz-plugins   
ii  compizconfig-backend-gconf
ii  compizconfig-settings-manager
ii  emerald
pi  libcompizconfig0
ii  libemeraldengine0
ii  python-compizconfig
```

and that's my xorg.conf:

```

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "it"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes	"1280x1024"
	EndSubSection
EndSection

```

ok, i guess that's enough.. .any hint? :)

tnx a lot :)

---

### Post by Forlong on 2008-05-25
Sounds like a setup issue to me. Here's how you can reset Compiz:
```
gconftool-2 --recursive-unset -a /apps/compiz
```
Afterwards restart Compiz like this
```
compiz
``` and see if it helped.

---

### Post by dsom on 2008-05-25
no luck, same error :(

tnx indeed :)

---

### Post by trebor on 2008-05-25
Try rebooting after you enable desktop effects.  I had a similar problem and that did the trick for me.

---

