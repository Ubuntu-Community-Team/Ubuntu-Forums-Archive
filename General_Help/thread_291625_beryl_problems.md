---
title: "beryl problems"
date: 2006-11-02
forum: General Help
---

### Post by DSn0wMan on 2006-11-02
I installed beryl following the instructions from this post [http://www.ubuntuforums.org/showthread.php?t=265678&highlight=Edgy+Compiz](http://www.ubuntuforums.org/showthread.php?t=265678&highlight=Edgy+Compiz)

It seems to work sometimes, but inevitably crashes my xserver. I get the following errors when launching beryl-manager:

josh@l33t-mobile:~$ libGL warning: 3D driver claims to not support visual 0x4b
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x4b
beryl: Plugin 'settings' already active
Initiating splash
beryl: water: GL_ARB_fragment_program is missing
No framebuffer_object support! (only simple blur aviable)
No fragment_program support! (only simple blur aviable)
No packed_depth_stencil support! (this may cause some artefacts in fbo mode)

FYI - I have a Radeon Mobility 300 (x300) video card, and I am using the open source radeon driver.

---

### Post by PriceChild on 2006-11-02
Have you got```
Option "AddARGBGLXVisuals" "True"
```In Section Screen in your xorg.conf ?

---

### Post by DSn0wMan on 2006-11-02
no, I don't seem to have any options set in my screen section.

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1152x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1152x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1152x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1152x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1152x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1152x768" "800x600"
	EndSubSection
EndSection

```

---

### Post by DSn0wMan on 2006-11-02
Added (Option "AddARGBGLXVisuals" "True") now I have a few less error messages, and it seems somewhat more stable.

josh@l33t-mobile:~$ beryl-manager
josh@l33t-mobile:~$ libGL warning: 3D driver claims to not support visual 0x4b
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x4b
Initiating splash
beryl: water: GL_ARB_fragment_program is missing

---

### Post by Toxicity999 on 2006-11-02
Actually you quoted the wrong area... should look more like

Section "Device"
    Identifier    "Generic Video Card"
    BusID        "PCI:1:0:0"
EndSection

That of course being a mock up. So what he was talking about insert there not under you're display settings ;)

also it appeared as thoug hyou already had beryl running that first time.

---

