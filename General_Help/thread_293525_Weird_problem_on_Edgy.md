---
title: "Weird problem on Edgy"
date: 2006-11-05
forum: General Help
---

### Post by MaliMedo2 on 2006-11-05
Every time I boot Edgy, just before login window pops up, my monitor goes out of frequency, then wait a couple of seconds, and everything is just fine after that.  Monitor is 20" LCD, and default resolution is 1680*1050@60 Hz. My xorg.conf is following:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"B102030W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Monitor		"B102030W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
	EndSubSection
EndSection
```

---

### Post by Engnome on 2006-11-05
Don't fix what isn't really broken. My monitor (with the same specs) uses wrong resolution at login screen. Take my advice it is hardly worth trying to fix.

---

### Post by Ramses de Norre on 2006-11-05
Hmm I don't think that's so healthy for your monitor.
I know you can configure the frequencies through HorizSync and VertRefresh options in xorg.conf but I'm not sure where to get the values.

---

