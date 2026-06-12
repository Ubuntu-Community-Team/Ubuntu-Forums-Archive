---
title: "Problem chaning resolution"
date: 2006-11-03
forum: General Help
---

### Post by I3roknI3ottle on 2006-11-03
ok my xorg.conf has this in it

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Accept, when I try to select a resolution under system>preferences>screen resolution, all that is there is 1280x1024, and I am able to do 1400x1050 in windows.  Why am I not allowed to select this?

---

### Post by klsmith259 on 2006-11-03
You need the package 915resolution i beleive. Are you on a laptop? I have no experience with this package or the resolution you are trying to achieve but I beleive this will solve you problems.

google 915resolution

---

