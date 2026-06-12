---
title: "My monitor is out of range"
date: 2008-06-25
forum: General Help
---

### Post by Myronray on 2008-06-25
**is there anybody can help to fix this problem.. everytime i restart my computer it says my monitor is out of range VF 60.0Hz / HF 64.1Khz, i installed my nvidia driver properly this is weird ehehe**


thanks and much appreciated

---

### Post by heyguy on 2008-06-25
i fixed this problem by editing xorg.conf file which is located at /etc/X11/xorg.cong .boot into recovery mode and go to root shell prompt,then type 
"nano /etc/X11/xorg.conf"  and look for section device. change it if something other that nvidia Inc. GeForce6200(here should be your video card model,mine is geforce6200)
driver  "nvidia"
and then write out to file and save changes and exit the editor.
after that type kdm or other display manager which you are using.
i think this will help
:)

---

### Post by Myronray on 2008-06-25
i try to edit my xorg look the config deatils 

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600 LE]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"AddARGBGLXVisuals" "True"
	Option 		"RenderAccel" "True"
	Option 		"AllowGLXWithComposite" "True"
	Option 		"backingstore" "True"
	Option 		"TripleBuffer" "True"
EndSection

it is correct?

thanks heyguy

---

