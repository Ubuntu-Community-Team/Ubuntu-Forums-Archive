---
title: "Can't get HDMI video to work"
date: 2013-09-21
forum: General Help
---

### Post by NikosF on 2013-09-21
HTPC with Ubuntu 12.04.3 LTS / 3.5.0-40-generic

Attached to LED LCD flatscreen and no video signal attached via HDMI.  Used to get a signal via VGA, but now just blank screen.  Video card is Nvidia GT220.

Any idea where to begin troubleshooting (clue Screen(s) found, but none have a usable configuration.)
 
-------------------------------
Excerpt from Xorg log:

[    19.704] (II) NVIDIA(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
[    19.704] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    19.704] (==) NVIDIA(0): RGB weight 888
[    19.704] (==) NVIDIA(0): Default visual is TrueColor
[    19.704] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    19.704] (**) NVIDIA(0): Option "NoLogo" "True"
[    19.704] (**) NVIDIA(0): Option "DPI" "100x100"
[    19.704] (**) NVIDIA(0): Enabling 2D acceleration
[    20.758] (II) NVIDIA(0): NVIDIA GPU GeForce GT 220 (GT216) at PCI:2:0:0 (GPU-0)
[    20.759] (--) NVIDIA(0): Memory: 1048576 kBytes
[    20.759] (--) NVIDIA(0): VideoBIOS: 70.16.31.00.00
[    20.759] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    20.762] (--) NVIDIA(0): Valid display device(s) on GeForce GT 220 at PCI:2:0:0
[    20.762] (--) NVIDIA(0):     CRT-0
[    20.762] (--) NVIDIA(0):     CRT-1
[    20.762] (--) NVIDIA(0):     DFP-0 (boot)
[    20.762] (--) NVIDIA(0):     DFP-1
[    20.762] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    20.762] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    20.762] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    20.762] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    20.762] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    20.762] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    20.762] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0
[    20.782] (EE) NVIDIA(0): Failing initialization of X screen 0
[    21.007] (II) UnloadModule: "nvidia"
[    21.007] (II) UnloadSubModule: "shadow"
[    21.007] (II) UnloadSubModule: "wfb"
[    21.007] (II) UnloadSubModule: "fb"
[    21.007] (EE) Screen(s) found, but none have a usable configuration.
[    21.007]
Fatal server error:
[    21.007] no screens found
[    21.007] (EE)
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
[    21.007] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    21.007] (EE)
[    21.008] Server terminated with error (1). Closing log file.

---

### Post by XBNCPRk on 2013-09-21
When you say no signal, do you mean the monitor is flashing 'no signal' as though it needs to be switched to another imput (ie from vga imput to hdmi) or youre just getting a blank black screen (ie a correct signal with no content)?

---

### Post by NikosF on 2013-09-22
> **XBNCPRk said:**
> When you say no signal, do you mean the monitor is flashing 'no signal' as though it needs to be switched to another imput (ie from vga imput to hdmi) or youre just getting a blank black screen (ie a correct signal with no content)?

Thanks for responding.  The monitor is flashing 'no signal'.  If I select another HDMI input (that the PC is not connected to) I just get a blank screen with no 'no signal' message flashing.  I assume that means the monitor is aware something is plugged in, but somehow it's not passing on the relevant information to the PC via the HDMI cable?

---

### Post by NikosF on 2013-09-22
My xorg.conf is pretty sparce.  I've not usually had to fiddle with xorg though since moving over from Fedora a few years back.

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Extensions"
        Option  "Composite"     "Disable"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "DPI"   "100x100"
        Option  "NoLogo"        "True"
EndSection

---
Are there any other log files I should be looking at?  dmesg?

---

### Post by XBNCPRk on 2013-09-22
I notice you mentioned > [COLOR=#000000][ 20.758] (II) NVIDIA(0): NVIDIA GPU GeForce GT 220 (GT216) at PCI:2:0:0 (GPU-0)[/COLOR] in your log, implying this is a new standalone video card and not integrated graphics used previously on a vga connection (?). 

In your BIOS, you may have to reorder the mobos preference for which video system it uses for output. Itll be listed (on mine at least) under the northbridge config settings, and look for anything that says PCI-GFXO-GPP-IGFX or some other combination thereof.
 
IGFX = any internal graphics chipset, GPP = gaming port, PCI = any PCI port with a graphics chip in it, and GFXO = primary PCI-E slot.

---

### Post by NikosF on 2013-09-23
I'll give that a try - thanks!

---

