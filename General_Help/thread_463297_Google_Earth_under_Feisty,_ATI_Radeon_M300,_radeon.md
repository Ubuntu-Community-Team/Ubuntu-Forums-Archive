---
title: "Google Earth under Feisty, ATI Radeon M300, radeon driver"
date: 2007-06-03
forum: General Help
---

### Post by Zeno Cosini on 2007-06-03
Under Breezy, I used the fglrx driver with my ATI Radeon M300 graphics card (on a Thinkpad T43). It worked like a charm. After switching to Feisty, I installed the radeon driver in a successful effort to get Beryl running. However, Google Earth is now *very* slow. For example, rotating the globe is very jerky. Also, when zooming in (which is also slow and jerky), Google Earth just increases the size of the pixels; only some time after the completing the zoom motion, it switches to the actual image.

The entry in the list shown by lspci is
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]

Direct rendering is definitely working:
glxinfo | grep direct
direct rendering: Yes

The "Device" section in xorg.conf reads:

Section "Device"
	Identifier	"ATI Technologies Inc M22 [Radeon Mobility M300]"
        Driver                "radeon"
        BusID                "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option "AGPMode" "8"  
        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
	Option "ColorTiling" "true" 
EndSection

Any ideas what is wrong?

---

