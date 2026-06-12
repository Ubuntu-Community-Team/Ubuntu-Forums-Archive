---
title: "Nvidia Problems"
date: 2005-10-21
forum: General Help
---

### Post by mwkenna on 2005-10-21
Here goes...
I have just installed Ubuntu 5.10 on a Toshiba P20-801 laptop
After installing the nvidia drivers through Synaptic (Misc graphics restricted) im getting some strange problems..

The nvidia drivers are loaded in xorg.conf, but the screen res wont go above 1024x768 (with the 'nv' drivers i am running 1400x900).

Getting a blank screen when logging out from Gnome or hitting ctrl+alt+backspace, no choice but to turn the power off and restart that way.

Hope someone can shed some light on the subject!
Thanks in advance, Mark.

---

### Post by chanders on 2005-10-21
Make sure in the "Screen" section you you have listed all the resolutions your monitor can show..... Here is my "Screen" section from my xorg.conf file.....

Yours will be different because you have a wide screen monitor...

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

```

---

### Post by mwkenna on 2005-10-22
Here is my xorg.conf


Section "Device"
        Identifier      "NVIDIA Corporation NV36 [GeForce FX Go 5700]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV36 [GeForce FX Go 5700]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection
EndSection

---

