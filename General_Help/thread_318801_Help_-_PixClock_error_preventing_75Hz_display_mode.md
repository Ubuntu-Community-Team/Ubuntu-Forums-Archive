---
title: "Help - PixClock error preventing 75Hz display mode"
date: 2006-12-14
forum: General Help
---

### Post by clubsoda on 2006-12-14
Looks like I'm stuck with a mildly flickering 60Hz refresh rate in 1280x1024 mode, apparently due to a misreading of the PixClock.  Hardware is a Matrox G550 (single head) DVI card driving a 19" LCD monitor.  Edgy has [known issues](https://bugs.launchpad.net/distros/ubuntu/+source/xserver-xorg-video-mga/+bug/58721) with the Matrox graphic card but I don't think these are the cause.

From my Xorg.log...
```
(II) MGA: driver for Matrox chipsets: mga2064w, mga1064sg, mga2164w,
        mga2164w AGP, mgag100, mgag100 PCI, mgag200, mgag200 PCI,
        mgag200 SE A PCI, mgag200 SE B PCI, mgag400, mgag550
(II) Primary Device is: PCI 01:00:0
(--) Chipset mgag550 found
.
(**) MGA(0): Depth 24, (--) framebuffer bpp 32
(==) MGA(0): RGB weight 888
(**) MGA(0): Option "UseFBDev" "True"
(**) MGA(0): Option "OldDmaInit" "True"
(==) MGA(0): Using AGP 1x mode
(==) MGA(0): Using XAA acceleration
(**) MGA(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
```So far, so good.  The framebuffer is a hack for the G550 bug in Edgy.```
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 0.0.2
        ABI class: X.Org Video Driver, version 1.0
(--) MGA(0): Linear framebuffer at 0xF2000000
(--) MGA(0): MMIO registers at 0xFE8FC000
(--) MGA(0): Pseudo-DMA transfer window at 0xFE000000
(--) MGA(0): BIOS at 0xFE8C0000
(II) Attempted to read BIOS 64KB from /sys/bus/pci/devices/0000:01:00.0/rom: got 36KB
(--) MGA(0): Video BIOS info block at offset 0x07D20
[COLOR="Red"](--) MGA(0): VideoRAM: 16384 kByte[/COLOR]

```There's one possible problem, since the card has 32MB.

```
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.0
(==) MGA(0): Write-combining range (0xf2000000,0x1000000)
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) MGA(0): I2C bus "DDC P1" initialized.
(II) MGA(0): I2C device "DDC P1:ddc2" registered at address 0xA0.
(II) MGA(0): I2C device "DDC P1:ddc2" removed.
(II) MGA(0): I2C Monitor info: 0x81fe690
(II) MG(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.0
(==) MGA(0): Write-combining range (0xf2000000,0x1000000)
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) MGA(0): I2C bus "DDC P1" initialized.
(II) MGA(0): I2C device "DDC P1:ddc2" registered at address 0xA0.
(II) MGA(0): I2C device "DDC P1:ddc2" removed.
(II) MGA(0): I2C Monitor info: 0x81fe690
(II) MGA(0): Manufacturer: MEL  Model: 4744A(0): Manufacturer: MEL  Model: 4744
(II) MGA(0): Year: 2006  Week: 28
(II) MGA(0): EDID Version: 1.3
(II) MGA(0): Digital Display Input
(II) MGA(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) MGA(0): Gamma: 2.20
(II) MGA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) MGA(0): Default color space is primary color space
(II) MGA(0): First detailed timing is preferred mode
(II) MGA(0): redX: 0.634 redY: 0.354   greenX: 0.287 greenY: 0.621
(II) MGA(0): blueX: 0.138 blueY: 0.077   whiteX: 0.313 whiteY: 0.329
(II) MGA(0): Supported VESA Video Modes:
(II) MGA(0): 720x400@70Hz
(II) MGA(0): 640x480@60Hz
(II) MGA(0): 640x480@67Hz
(II) MGA(0): 640x480@72Hz
(II) MGA(0): 640x480@75Hz
(II) MGA(0): 800x600@56Hz
(II) MGA(0): 800x600@60Hz
(II) MGA(0): 800x600@72Hz
(II) MGA(0): 800x600@75Hz
(II) MGA(0): 832x624@75Hz
(II) MGA(0): 1024x768@60Hz
(II) MGA(0): 1024x768@70Hz
(II) MGA(0): 1024x768@75Hz
(II) MGA(0): 1280x1024@75Hz
(II) MGA(0): 1152x870@75Hz
(II) MGA(0): Manufacturer's mask: 0
(II) MGA(0): Supported Future Video Modes:
(II) MGA(0): #0: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) MGA(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) MGA(0): #2: hsize: 1280  vsize 1024  refresh: 66  vid: 34433
(II) MGA(0): #3: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
(II) MGA(0): #4: hsize: 1024  vsize 768  refresh: 66  vid: 18017
(II) MGA(0): #5: hsize: 1152  vsize 864  refresh: 70  vid: 19057
(II) MGA(0): #6: hsize: 1280  vsize 960  refresh: 75  vid: 20353
(II) MGA(0): #6: hsize: 1280  vsize 960  refresh: 75  vid: 20353
[COLOR="Red"](II) MGA(0): #7: hsize: 1280  vsize 1024  refresh: 75  vid: 36737[/COLOR]
```Look, the monitor says it can do it!

```
(II) MGA(0): Supported additional Video Mode:
(II) MGA(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) MGA(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) MGA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) MGA(0): Ranges: V min: 55  V max: 76 Hz, H min: 31  H max: 81 kHz, [COLOR="Red"]PixClock max 130 MHz[/COLOR]
```Where does this number come from?  It's wrong.

```
(II) MGA(0): Monitor name: RDT194LM
(II) MGA(0): end of I2C Monitor info
(==) MGA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) MGA(0): Min pixel clock is 12 MHz
(--) MGA(0): Max pixel clock is 1200 MHz
(II) MGA(0): Mitsubishi RDT194LM: Using hsync range of 31.50-81.10 kHz
(II) MGA(0): Mitsubishi RDT194LM: Using vrefresh range of 56.00-76.00 Hz
(II) MGA(0): [COLOR="Red"]Clock range:  12.00 to 1200.00 MHz[/COLOR]
```That's more like it!  But it's too late - here come the errors:-```
(WW) (1280x1024,Mitsubishi RDT194LM) mode clock 135MHz exceeds DDC maximum 130MHz
(WW) (1280x1024,Mitsubishi RDT194LM) mode clock 157.5MHz exceeds DDC maximum 130MHz
(II) MGA(0): Not using default mode "1280x1024" (hsync out of range)
etc
etc
```The monitor is a recent model.  Does it have to be included in some database?

I installed **xresprobe** and ran **ddcprobe** to see what was coming back from the monitor.  Its output looks like this:-```
vbe: VESA 3.0 detected.
oem: Matrox Graphics Inc.
vendor: Matrox
product: Matrox G550 00
[COLOR="Green"]memory: 32768kb[/COLOR]
mode: 640x480x256
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x16
mode: 800x600x256
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x256
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x32k
mode: 1280x1024x64k
[COLOR="Blue"]mode: 1280x1024x16m[/COLOR]
edid: 
edid: 1 3
id: 4744
eisa: MEL4744
serial: 01010101
manufacture: 28 2006
[COLOR="Red"]input: analog signal.[/COLOR]
screensize: 38 30
gamma: 2.200000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
[COLOR="Blue"]timing: 1280x1024@75 (VESA)[/COLOR]
ctiming: 1280x960@60
ctiming: 1280x1024@60
ctiming: 1280x1024@66
[COLOR="Blue"]ctiming: 1280x1024@76[/COLOR]
ctiming: 1024x768@66
ctiming: 1152x864@70
ctiming: 1280x960@75
[COLOR="Blue"]ctiming: 1280x1024@75[/COLOR]
[COLOR="Blue"]dtiming: 1280x1024@70[/COLOR]
monitorrange: 31-81, 55-76
monitorname: RDT194LM
```The "analog signal" part is wrong but everything else looks OK.  What can I do to get those blue modes working, any suggestions?

---

### Post by majoridiot on 2006-12-14
try adding:

```
Option UseEDID "False"
```

to your xorg.conf video Device section and adding a modeline with the correct resolution and 
frequency to your monitor definition and see if it makes a difference.

if you need help determining the correct modeline to use, open a terminal and type gtf.

hope that helps :)

---

### Post by clubsoda on 2006-12-14
That's a rather ugly hack, but I'm willing to give it a go. :) 
Here are the modified sections of xorg.conf:-```
Section "Device"
        Identifier      "Matrox G550"
        Driver          "mga"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "True"
        Option          "OldDmaInit"            "True"
        Option          "UseEDID"               "False"
EndSection

Section "Monitor"
        Identifier      "Mitsubishi RDT194LM"
        Option          "DPMS"
        HorizSync       31.5-81.1
        VertRefresh     56-76
        UseModes        "Modes[0]"
EndSection

Section "Modes"
        Identifier      "Modes[0]"
 # 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
  Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
  # 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
  Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
  # 800x600 @ 75.00 Hz (GTF) hsync: 47.02 kHz; pclk: 48.91 MHz
  Modeline "800x600_75.00"  48.91  800 840 920 1040  600 601 604 627  -HSync +Vsync 
  # 640x480 @ 75.00 Hz (GTF) hsync: 37.65 kHz; pclk: 30.72 MHz
  Modeline "640x480_75.00"  30.72  640 664 728 816  480 481 484 502  -HSync +Vsync
EndSection 
```The Screen section is as it was, with resolutions listed but no refresh rates.

After a reboot, no change.  Still running 60Hz, and the list of options in the Display Settings  menu hasn't changed.  The Xorg log looks very similar to how it was before, i.e. everything is still getting probed.  The Modelines are then acknowledged but aren't being applied. :???:

---

### Post by clubsoda on 2006-12-14
Just noticed this near the end of the Xorg.0.log:-```
(WW) MGA(0): Option "UseEDID" is not used
```So I tried this instead.```
        Option          "IgnoreEDID"            "1"
```

Same deal.
](*,)

---

