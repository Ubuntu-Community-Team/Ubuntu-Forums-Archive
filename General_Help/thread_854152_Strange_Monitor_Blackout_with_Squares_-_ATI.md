---
title: "Strange Monitor Blackout with Squares - ATI"
date: 2008-07-09
forum: General Help
---

### Post by djxcon on 2008-07-09
I have been reluctant to start a thread about this but it is finally getting the best of me.  I am running Ubuntu Hardy Heron and using an ATI video card (ATI Technologies Inc RV350 AP [Radeon 9600]). This never happened in Feisty.  Compiz is turned on but not certain that this is causing the issue. Kernel - Linux ubuntu 2.6.24-19-rt. Monitor = Samsung SyncMaster 931bf.

The Issue:
Whenever I am just clicking around on the computer, mainly FireFox 3, the screen all of a sudden goes completely black with white squares on it (see attachment).  This happens most often when I am using FireFox but has happened on other applications as well. Most recently, I clicked on one of my bookmarks in FireFox and the screen went black.  This is not reproducible but it happens unexpectedly almost daily. 

The Workaround. 
I can work around the problem in three ways that I know of.  
1) Press Alt F1 and then Alt F7.  This returns me back to where I was before the problem happened and is the best resolution so far.
2) Crtl Alt Backspace and then log back in.
3) Reboot

xorg.conf file:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

I have looked through the logs but haven't found anything that seems related.  Perhaps I am looking in the wrong log file?  Any help would be greatly appreciated.

---

### Post by djxcon on 2008-07-09
Does anyone feel that this should be reported as a bug to Launchpad?  Is there a compiz log that I am not seeing that may be useful in debugging this issue?

---

### Post by djxcon on 2008-07-10
Well it just happened again and I might have something useful in the Xorg log.  Anyone know how to interpret these messages?

After the problem, I had to Cntl Alt F1 and then Cntl Alt F7 to get back to the System Log viewer. 

```
(II) AIGLX: Suspending AIGLX clients for VT switch
disable montype: 1
disable montype: 3
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000 0xe7ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xe7ffe000 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xf87ff800
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
disable montype: 3
init memmap
init common
init crtc2
init pll2
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xe7ffe000 0xe7ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xf87ff800
restore common
restore crtc2
restore pll2
finished PLL2
restore FP
enable montype: 3
(II) RADEON(0): [RESUME] Attempting to re-init Radeon hardware.
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): [agp] Mode 0x1f000207 [AGP 0x8086/0x1a30; Card 0x1002/0x4150]
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xe7ffe000 is: 0xe7ffe000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xf87ff800 is: 0xf87ff800
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xe7ffe000 0xe7ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xf87ff800
enable montype: 1
enable montype: 3
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

---

### Post by djxcon on 2008-07-13
Well, I have posted this issue here and in Launchpad but have not had any luck getting a response.  I am posting an update to the issue to see if anyone can assist given the new information. 

This problem has happened with Compiz turned off so we can rule that out.  I have updated my xorg.conf to the following but the problem just happened so this also did not help. 

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9600"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

---

### Post by djxcon on 2008-07-21
Even though I have been very consistent in replying to myself (HAHA), I figured that I would provide the last update to this thread.  I believe that this problem was due to a faulty GPU on the video card.  I have reverted back to a GeForce 2 card for about a week now without a problem.

---

