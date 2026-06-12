---
title: "Screen resolution"
date: 2007-10-04
forum: General Help
---

### Post by octotom on 2007-10-04
Hi,

I'm sure you've heard it a bagillion times before, but I can't get the screen resolution on Ubuntu Feisty (7.04, I believe) to get where I want.  The highest level that I can choose is 1024x786.  I want 1280x1024, which is what I had on windows before I 'converted'.

I'll paste that xorg.conf file that seems to always be needed.  I tried to make changes before but I couldn't because it was read-only.

Here it is:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection

I'd like to get this rectified because, I'm falling in love with Ubuntu, but the un-sharpness of things is kinda putting a damper on it.

Thanks in advance
Tom

PS  Are there any good internet security things that I could install for Ubuntu?

---

### Post by zvacet on 2007-10-04
[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

