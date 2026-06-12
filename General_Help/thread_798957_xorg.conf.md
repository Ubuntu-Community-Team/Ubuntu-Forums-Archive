---
title: "xorg.conf"
date: 2008-05-18
forum: General Help
---

### Post by milanvora2 on 2008-05-18
Hi,

I need some help fine-tuning my xorg.conf
Initially I had all the hashes removed (but the image flickered when i watched a movie)
By disabling the options, the image doesn0t flicker which watching a video, but while rotating the cube it refreshes on some lines slowly and i have used compiz effects previously without such problems.
I have a aTI Radeon 3650 card and I am using the ati proprietary drivers installed with envy
Any idea on what my config should look like


Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
#	Option          "XAANoOffscreenPixmaps" "1"
#        Option          "TexturedVideo" "1"
#	Option		"TexturedVideoSync"	"1"
#       Option          "UseFastTLS"    "1"
#        Option          "BackingStore"  "1"
#        Option          "Textured2D"    "1"
#        Option          "TexturedXRender"       "1"
#        Option          "BackingStore"  "1"
#        Option          "AccelMethod"   "EXA"
#       Option          "DRI"   "1"
#        Option          "DynamicClocks" "1"
#        Option          "ForceGenericGPU"       "0"
        Option          "VideoOverlay"  "0"
        Option          "OpenGLOverlay" "0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"1280x1024"
	EndSubSection
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

