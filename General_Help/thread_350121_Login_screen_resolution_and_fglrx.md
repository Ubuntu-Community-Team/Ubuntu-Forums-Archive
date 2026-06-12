---
title: "Login screen resolution and fglrx"
date: 2007-01-31
forum: General Help
---

### Post by emsiv82 on 2007-01-31
Hi!

I've a problem with login screen resolution, **since I've installed fglrx drivers**. The login screen is displayed at 1280x1024 resolution, instead of 1024x768.

I've read some post around here, so I looked in my xorg.conf:

```

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Monitor    "VIDEOSEVEN"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

Login screen is still at 1280 :(

Thank you! :)

---

### Post by maxwellcom on 2007-02-13
emsiv82,

[http://ubuntuforums.org/showthread.php?t=359310]("http://ubuntuforums.org/showthread.php?t=359310")

hope it helps

---

