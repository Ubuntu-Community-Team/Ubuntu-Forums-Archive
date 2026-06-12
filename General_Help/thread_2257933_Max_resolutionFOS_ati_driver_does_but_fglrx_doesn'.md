---
title: "Max resolution:FOS ati driver does but fglrx doesn't"
date: 2014-12-23
forum: General Help
---

### Post by ozooha on 2014-12-23
My OS is Lubuntu 14.40 and my monitor is SAMSUNG 4K TV. The ATI open source driver gives me the max resolution 3849x2160 at 30Hz refresh rate but not the fglrx-updates driver.
The connection cable is HDMI. I tried using the xrandr approach as provided in the link -https://wiki.ubuntu.com/X/Config/Resolution without success.
It complained:
> 
cvt 3840 2160 30
# 3840x2160 29.98 Hz (CVT) hsync: 65.96 kHz; pclk: 338.75 MHz
Modeline "3840x2160_30.00"  338.75  3840 4080 4488 5136  2160 2163 2168 2200 -hsync +vsync

xrandr --newmode "3840x2160_30.00"  338.75  3840 4080 4488 5136  2160 2163 2168 2200 -hsync +vsync

xrandr --addmode DFP1 3840x2160_30.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  39
  Current serial number in output stream:  40

Below are some of the information which might help I believe.
Driver name:

> lsmod | grep -E 'nvidia|nouveau|i915|radeon|fglrx'
fglrx                9233277  119 
amd_iommu_v2           18903  1 fglrx


> lspci -nnk | grep -iA2 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7480D] [1002:9993]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7793]
	Kernel driver in use: fglrx_pci

Link to Xorg.0.log file: [http://paste.ubuntu.com/9605086/](http://paste.ubuntu.com/9605086/)
Below are the xrandr -q for both the drivers
ATI open source:
> Screen 0: minimum 320 x 200, current 3840 x 2160, maximum 16384 x 16384
DisplayPort-0 connected 3840x2160+0+0 (normal left inverted right x axis y axis) 1872mm x 1053mm
   4096x2160      24.0     24.0  
   3840x2160      30.0*    25.0     24.0     30.0     24.0  
   1920x1080      60.0     50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1920x1080i     60.1     50.0     60.0  
.....
fglrx:
> Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
DFP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 1872mm x 1053mm
   1920x1080      60.0*+   50.0     59.9     60.1     50.0     30.0     25.0     24.0     60.0     30.0     24.0  
   1776x1000      50.0     59.9     50.0     25.0     24.0     60.0     30.0  
   1680x1050      60.0  
....

> cannot access /etc/X11/xorg.conf: No such file or directory


So do I conclude that the fglrx doesn't work? or am I doing something stupid..steer me in the right direction if possible.
Much appreciated.
OZooHA

---

### Post by DuckHook on 2014-12-23
You are not doing anything stupid. In fact, you are to be commended for posting with this much background research and info. It makes it easy to help.

The *HD 7480D* is a GPU integrated into your CPU that steals from system RAM for VRAM and with RAM bus speed throughput, which is to say, very slow. It is a low-end chipset designed for value laptops that is only supposed to support a max resolution of 2560x1600. That you could get 4K TV resolution using the *radeon* driver is a very pleasant surprise (I didn't know the FOSS driver was that versatile&#8213;you learn something new every day) and is likely due to your setting refresh rate at 30 fps and/or colour depth at less than optimal, which is in eye-strain/headache-inducing territory.

The simple answer to your problem is that *fglrx* is not designed to operate at 30 fps and/or 16-bit colour depth and doesn't give you the option to do so for this chipset. *radeon* most surprisingly is, so you can trade refresh rate/colour depth for higher resolution.

If your computer is a desktop and you are intent on 4K HD resolution, you can install a new and proper video card that has high resolution support and disable the on-chip *HD 7480D*. If it's a laptop and you still want to use *fglrx*, then you can try monkeying around with reduced colour depth & refresh rate (though I doubt that *fglrx* will give you a 4K HD option no matter how you tweak it), or you can live with HD resolution which is not actually that bad, as your TV will just display the signal on a straight four to one pixel interpolation. This should yield minimal artifacts. Or, you could just live with the *radeon* driver which, given the low power of your card, may be all it can handle anyway.

I'm afraid there is no answer for your combination of existing equipment that doesn't involve one of the above compromises.

---

### Post by ozooha on 2014-12-24
Thank you DuckHook for your insights. My desktop is primarily a XBMC HTPC and the refresh rate doesn't get in the way of providing sharp images.
I tired the fglrx equivalent on WIN 8 and it worked but after using a software which overrides the EDID information. I was therefore hoping the 
xrandr would do the EDID trick in Linux.
Thank you though for your thoughts which are much appreciated.
OZooHA

---

