---
title: "ubuntu 16.04 + Radeon + displaylink problem"
date: 2016-10-07
forum: General Help
---

### Post by suikula on 2016-10-07
Hi

Im having problems with my ubuntu 16.04 laptop.. My laptop is using 
```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7550M/7570M/7650M]
```

Modules:
```
# lsmod | grep -i radeon
radeon               1515520  8
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
drm_kms_helper        147456  2 evdi,radeon
drm                   364544  18 ttm,evdi,drm_kms_helper,radeon

```

```
# modinfo radeon |head -n 1
filename:       /lib/modules/4.4.0-38-generic/kernel/drivers/gpu/drm/radeon/radeon.ko
```

I have downloaded and istalled newest displaylink drivers from [http://www.displaylink.com/downloads/ubuntu]("http://www.displaylink.com/downloads/ubuntu") . Radeon drivers are working really nicely when only using laptop monitor, but when I try to use external monitor Im experiencing weird lag and horizontal tearing.
For example, if Im operating in terminal - sometimes executing command with enter wont refresh the screen.. I have to press another key to make refresh to happen..When scrolling internet pages I have horizontal tearing..

Im using i3 wm.. but same thing happens with gnome and other wm/desktop environments.

Any help ?

---

### Post by DuckHook on 2016-10-07
You don't mention whether the displaylink drivers improve anything or if the results are the same as with just stock radeon. It is unlikely that your displaylink drivers are really anything other than the stock radeon with some added Dell proprietary bits for USB support.

To my knowledge, there are no other drivers for AMD other than the stock radeon because AMD no longer supports proprietary drivers for the newer Xorg implementation that is used in Xenial. This extends back to 14.04.5, so if you want to use AMD's old proprietary drivers, you will have to reinstall 14.04.4 and no later. Therefore, displaylink drivers cannot magically work better in 16.04 because it is highly doubtful that Dell bothered to write complicated video drivers for the small Linux customer base that they have.

Due to even the small amount of tinkering that Dell would have made to their displaylink drivers, I don't know how to help you with them. However, if you are running the stock radeon, then post results of:```
lspci -vk | grep -iA13 vga | grep driver
``````
xrandr -q
``````
sudo apt install read-edid && sudo get-edid | parse-edid
```I suspect that the problem is not with the video driver, but with the way Dell implements USB display, which is out of my league. You may have no choice but to run 14.04.4 using fglrx.

---

### Post by QIII on 2016-10-07
There are also the open source AMDGPU driver and the closed source AMDGPU-Pro driver, but I don't think support extends back to the HD 7000 models yet.

---

### Post by DuckHook on 2016-10-07
> **QIII said:**
> There are also the open source AMDGPU driver and the closed source AMDGPU-Pro driver, but I don't think support extends back to the HD 7000 models yet.Thanks, QIII.

I would be *very* interested in that for my HD 7950, but I wasn't aware that the driver was being extended back to older cards. I was under the impression that the 7000 series was only going to be supported by radeon.

If not, then good news. Any idea of ETA?

---

### Post by suikula on 2016-10-11
> **DuckHook said:**
> You don't mention whether the displaylink drivers improve anything or if the results are the same as with just stock radeon. It is unlikely that your displaylink drivers are really anything other than the stock radeon with some added Dell proprietary bits for USB support.

To my knowledge, there are no other drivers for AMD other than the stock radeon because AMD no longer supports proprietary drivers for the newer Xorg implementation that is used in Xenial. This extends back to 14.04.5, so if you want to use AMD's old proprietary drivers, you will have to reinstall 14.04.4 and no later. Therefore, displaylink drivers cannot magically work better in 16.04 because it is highly doubtful that Dell bothered to write complicated video drivers for the small Linux customer base that they have.

Due to even the small amount of tinkering that Dell would have made to their displaylink drivers, I don't know how to help you with them. However, if you are running the stock radeon, then post results of:```
lspci -vk | grep -iA13 vga | grep driver
``````
xrandr -q
``````
sudo apt install read-edid && sudo get-edid | parse-edid
```I suspect that the problem is not with the video driver, but with the way Dell implements USB display, which is out of my league. You may have no choice but to run 14.04.4 using fglrx.

Thank you for reply.. Sorry for the delay to reply back.. Without the display driver I cannot get external monitor to work at all. 
Here are the results for the commands you told me..
```
# lspci -vk | grep -iA13 vga | grep driver
	Kernel driver in use: radeon

```

```
# xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
LVDS connected (normal left inverted right x axis y axis)
   1600x900      60.00 +  40.00  
   1440x900      59.89  
   1280x854      59.89  
   1280x800      59.81  
   1280x720      59.86  
   1152x768      59.78  
   1024x768      59.92  
   800x600       59.86  
   848x480       59.66  
   720x480       59.71  
   640x480       59.38  
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
DisplayPort-2 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected primary 1920x1080+0+0 509mm x 286mm
   1920x1080     60.00*+
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1024x768      75.08    60.00  
   800x600       75.00    60.32    56.25  
   848x480       60.00  
   640x480       75.00    60.00    59.94  
   720x400       70.08  

```

```
# get-edid | parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
No EDID on bus 5
No EDID on bus 7
No EDID on bus 8
No EDID on bus 9
No EDID on bus 10
2 potential busses found: 0 6
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
128-byte EDID successfully retrieved from i2c bus 0
If this isn't the EDID you were looking for, consider the other potential busses.
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
	Identifier " 
                     @"
	ModelName " 
                    @"
	VendorName "LGD"
	# Monitor Manufactured week 0 of 2010
	# EDID version 1.4
	# Digital Display
	DisplaySize 310 170
	Gamma 2.20
	Option "DPMS" "false"
	Modeline 	"Mode 0" 121.20 1600 1760 1856 2158 900 903 908 936 -hsync -vsync 
	Modeline 	"Mode 1" 80.80 1600 1760 1856 2158 900 903 908 936 -hsync -vsync 
EndSection

```

---

### Post by suikula on 2016-10-12
Any one has any ideas how to get the actual diplaylink port to work ? If I attache monitor to displaylink port ubuntu wont recognize external monitor at all.

---

