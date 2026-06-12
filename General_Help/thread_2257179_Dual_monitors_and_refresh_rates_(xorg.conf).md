---
title: "Dual monitors and refresh rates (xorg.conf)"
date: 2014-12-17
forum: General Help
---

### Post by manilaboy1vic on 2014-12-17
I am looking for help on a dual monitor setup.. One is an old DELL monitor, one is a fairly recent ASUS.

Im looking to have the ASUS be the primary monitor.. (everytime I boot up the orientation is wrong, the DELL is to the LEFT of the ASUS physically, when i boot up and move my mouse left, I hit a wall, have to go into settings <> displays to fix, Every reboot.)

Also I need my ASUS refresh rate to be 144hz.. I can run:

```

xrandr -s 1920x1080 -r 144 

```

and that seems to adjust the refresh rate, but then the DELL monitors screen turns off, back to settings <> displays, need to turn it back on..

Reason for the 144hz and primary on the ASUS, to play games on steam at with a good refresh rate.

Right now I just have a working xorg.conf file, ive put in effort to make sense of it but cant really.. 

I have run aticonfig --inital=dual-head and tried to set the modes and but its ends up breaking the screen on the ASUS.. even the vanila aticonfig --inital=dual-head config breaks the ASUS.

This is the xorg.conf file that is currently in place:

```

[jcv@jcvuntu-pc ~] cat /etc/X11/xorg.conf
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection


Section "Module"
EndSection


Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection


Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection


Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


[jcv@jcvuntu-pc ~] 

```

I can post the xrandr when I get home.  Monitors are off now, sitting at work.

```

[jcv@jcvuntu-pc ~] xrandr -q
Can't open display 

```

Drivers:
```

[jcv@jcvuntu-pc ~] lsmod | grep fgl
fglrx               11076428  81 
amd_iommu_v2           19054  1 fglrx



```

I installed the the new amd omega  drivers on a r9 290x if that matter.

Would truly appreciate the assistance..

Thanks,

jv

---

### Post by manilaboy1vic on 2014-12-18
Well I made some progress. I figured out the refresh rate and setting the primary monitor, still cannot get the positioning right.. so close, bah:


With this code.. I still need to go into Settings <> Displays and fiddle with the monitoring positioning..

```


 Section "ServerLayout"	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection


Section "Module"
EndSection


Section "Monitor"
	Identifier   "DFP7"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "144"
	Option	    "Primary" "true"
	Option	    "DPMS" "true"
EndSection


Section "Monitor"
	Identifier   "DFP6"
	Option	    "LeftOf" "DFP7"
	Option	    "PreferredMode" "1680x1050"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection


Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection


Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by manilaboy1vic on 2014-12-18
No matter what I set as the "Primary" monitor, If i move the top Gnome bar, wherever that bar is, is primary, confirmed with xrandr.

---

### Post by manilaboy1vic on 2014-12-18
Issue resolved.. running Gnome Ubuntu 14.10, just upgraded via the software center.

---

