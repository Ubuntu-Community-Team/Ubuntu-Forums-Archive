---
title: "ati 9250 open source radeon drivers"
date: 2006-10-29
forum: General Help
---

### Post by Architeuthis on 2006-10-29
Hello i have an ati radeon 9250 Pro, the fglrx drivers contain bugs and are no longer supported for my card. So i tried the open source radeon drivers.
But they give me this error every time i start a 3d application:
> drmCommandWrite: -22
drmRadeonCmdBuffer: -22 (exiting)

This is my device output in my xorg.conf file:
> Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver		"radeon"
	Option          "AGPMode"       "4"
        BusID		"PCI:1:0:0"
        Option          "ColorTiling" "on"
        Option          "AccelMethod" "EXA"
        Option          "XAANoOffscreenPixmaps"
        Option          "RenderAccel" "true"
EndSection

Does anyone else use the radeon opensource drivers for an ati radeon 9250 pro, with 3d accelaration enabled? If so can you please post your xorg.conf output, so i can copy it? Has anyone else ever had this error before? Searching it on google gave me no useful information, it seems people get the same error in completley different circumstances on different os's like bsd.

---

### Post by mrv on 2006-12-16
(moderators might want to merge some if these subjects). Works for most people, but should work for you too with kernel 2.6.19. See [another post](http://ubuntuforums.org/showpost.php?p=1893660&postcount=5).

---

