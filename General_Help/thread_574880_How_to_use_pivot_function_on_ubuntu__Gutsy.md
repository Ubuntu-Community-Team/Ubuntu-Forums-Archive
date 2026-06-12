---
title: "How to use pivot function on ubuntu : Gutsy?"
date: 2007-10-13
forum: General Help
---

### Post by ehdtkqorl123 on 2007-10-13
I have 24 inch monitor that has pivot function.
IT works well on Windows.
Now I want to use in for ubuntu so 

I opened xorg.conf and changed to the following:
[B]
Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8500 GT]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option "RandRRotation"		"on"
EndSection[/B]

My graphic card is 256MB Nvidia Geforce 8500GT..

Now I restarted my com and went to systems/preferences/screen resolution.
I see the third field named Rotation but it is DISABLED.. so i cannot select right or left..

When I execute xrandr -o right, it says

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)


So I have no idea what is wrong... Please help me..

---

### Post by smurtguy on 2007-10-14
the option for randr

option "RandRRotation" "on" 

does not go in the device section 

move it to the screen section instead

here is the section from my xorg.conf

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34M [GeForce FX Go5200 32M/
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
**    Option "RandRRotation"  "true"**
    SubSection     "Display"
        Depth       24
        Modes      "1400x1050"
    EndSubSection
EndSection

---

