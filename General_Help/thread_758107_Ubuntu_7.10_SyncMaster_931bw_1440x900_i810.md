---
title: "Ubuntu 7.10 SyncMaster 931bw 1440x900 i810"
date: 2008-04-17
forum: General Help
---

### Post by ivanstojkovic on 2008-04-17
Hello,

i have Ubuntu 7.10, Symsung SyncMaster 931bw and i810 integrated Graphic Card. I cannot get ubuntu do 1440x900 ond 75Hz. I only get 1280x1024 on 75Hz.

In my xorg i have tried this:

Section "Monitor"
        Identifier      "SyncMaster"
        Vendorname      "Samsung"
        Modelname       "SyncMaster 931BW , SyncMaster Magic CX931BW (Analog)"
        Horizsync       30-81
        Vertrefresh     56-75
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82945G/GZ Integrated Graphics Controller"
        Monitor         "SyncMaster"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1920    1200
                Modes           "1440x900@75"   "1440x900@60"
        EndSubSection
EndSection



.... so i removed all other options, but it still doesn't work

Does anyone have this problem also?

---

### Post by DracoZA on 2008-04-18
I am running 931BW on Geforce via MSI onboard which runs 1440*900 no problem, however it runs @ 50hz

Xorg.conf

Section "Monitor"
	
Identifier	"SyncMaster"
	
Option		"DPMS"
	
Horizsync	30-81
	
Vertrefresh 	60-75

EndSection

Section 

Section "Screen"
	
Identifier "Default Screen"
	
Device		"nVidia Corporation C51PV [GeForce 6150]"
	
Monitor		"SyncMaster"
	
Defaultdepth	24
	
SubSection "Display"
		
Modes		"1440x900"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	

EndSubSection

EndSection

Section 

I hope it helps

---

