---
title: "How can I get Ubuntu 16.04 to use my external monitor's native resolution?"
date: 2016-07-29
forum: General Help
---

### Post by snaysler on 2016-07-29
My external monitor is an HDMI LCD screen with 2560x1440 resolution. My laptop is the "MSI GT72 2QE/Dragon Edition" listed on page two of [https://www.msi.com/pic/faq/10015790@2015-0709-0531-323792@faq_0000000001661_en.pdf](https://www.msi.com/pic/faq/10015790@2015-0709-0531-323792@faq_0000000001661_en.pdf), which is a document specifying the maximum external monitor resolutions for my system. My laptop screen is a 1080p LCD screen. I'm using the external monitor in a dual monitor set-up no problem, except that the external monitor is running at 1920x1080. It's doesn't look awful, but I really wanted to use its native resolution quality.

When I go to Displays in System Settings, 1080p is the highest resolution option available for my monitor. The external monitor is again a 2560x1440 Dell 27" LCD monitor. What can I do to fix this? Help would be uber appreciated

---

### Post by papibe on 2016-07-29
Hi snaysler.

Could you open a terminal, run these commands, and post back the results? (you can copy paste the text):
```
lspci -nnk | grep -iA2 vga

lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau'

xrandr --q1

xrandr --q12

xvidtune -show
```
Regards.

---

### Post by Bucky Ball on 2016-07-29
Are you running a driver for it? Have you looked in 'Additional Drivers'?

Look forward to the output from papibe's commands.

---

### Post by richlion2 on 2016-07-30
It seems like your laptops has a GTX Nvidia graphics card. Correct? 

On Ubuntu 15 for Nvidia I had to enable a recommended Nvidia driver and connect my external screen to an HDMI port. I would not able to connect an external screen with the generic driver that is shipped with the Ubuntu installation.
But don't know how this works in Ubuntu 16. When I launch the System Settings other drivers option nothing happens, it gets stuck on a message "gathering system info".

On Ubuntu 15 everything worked nicely and you could also install [COLOR=#000000]nvidia-settings[/COLOR] to change your Nvidia graphics settings, including an external screen.

Regards
Rich

---

### Post by Bucky Ball on 2016-07-30
You mean Additional Drivers? Give it time. It takes a little while to gather information. It doesn't happen instantly. It might take a minute or more.

---

### Post by snaysler on 2016-08-02
> **papibe said:**
> Hi snaysler.

Could you open a terminal, run these commands, and post back the results? (you can copy paste the text):
```
lspci -nnk | grep -iA2 vga

lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau'

xrandr --q1

xrandr --q12

xvidtune -show
```
Regards.

Here's what I got:

```

snaysler@tayler-ubuntu:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM204M [GeForce GTX 980M] [10de:13d7] (rev a1)
	Subsystem: Micro-Star International Co., Ltd. [MSI] GM204M [GeForce GTX 980M] [1462:1129]
	Kernel driver in use: nvidia
snaysler@tayler-ubuntu:~$ lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau'
nvidia_uvm            659456  0
intel_powerclamp       16384  0
kvm_intel             172032  0
kvm                   536576  1 kvm_intel
nvidia_drm             45056  1
nvidia_modeset        765952  5 nvidia_drm
aesni_intel           167936  4
drm_kms_helper        147456  1 nvidia_drm
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
drm                   360448  4 drm_kms_helper,nvidia_drm
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
nvidia              11247616  80 nvidia_modeset,nvidia_uvm
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
btintel                16384  1 btusb
bluetooth             520192  10 bnep,ath3k,btbcm,btrtl,btusb,btintel
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
snaysler@tayler-ubuntu:~$ xrandr --q1
 SZ:    Pixels          Physical       Refresh
*0   3840 x 1080   ( 762mm x 211mm )  *50  
 1   1680 x 1050   ( 333mm x 205mm )   51  
 2   1440 x 900    ( 285mm x 175mm )   52  
 3   1366 x 768    ( 271mm x 150mm )   53  
 4   1280 x 1024   ( 254mm x 200mm )   54  
 5   1280 x 800    ( 254mm x 156mm )   55  
 6   1280 x 720    ( 254mm x 140mm )   56  
 7   1024 x 768    ( 203mm x 150mm )   57  
 8    800 x 600    ( 158mm x 117mm )   58  
 9    640 x 480    ( 127mm x  93mm )   59  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - X Axis Y Axis
snaysler@tayler-ubuntu:~$ xrandr --q12
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 16384 x 16384
HDMI-0 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 597mm x 336mm
   1920x1080     60.00*+  59.94    50.00    23.97    60.05    60.00    50.04  
   1680x1050     59.95  
   1600x1200     60.00  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00    50.08  
   720x480       59.94    60.05  
   640x480       75.00    59.94    59.93  
DP-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
   1920x1080     60.01*+
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
snaysler@tayler-ubuntu:~$ xvidtune -show
"3840x1080"   148.50   3840 2008 2052 2200   1080 1082 1087 1125 +hsync +vsync



```

I looked under additional drivers, and there are many options for nvidia drivers, but I'm using the latest working one. Other than that, no other additional drivers are listed. I am using my HDMI port, have the latest nVidia drivers, etc.

---

### Post by papibe on 2016-08-02
Thanks.

Since you are already using the Nvidia driver, you should try to setup your monitor using 'Nvidia X Server Settings', not 'Displays'.

If that does not work, let's try to get more information. Please install this package:
```
sudo apt-get install read-edid
```
Then using the method described [here]("http://nvidia.custhelp.com/app/answers/detail/a_id/3571/~/managing-a-display-edid-on-linux") obtain the 2 EDIDs from each monitors (note that they are binary files). Then please run these commands and post back the results:
```
nvidia-settings -q CurrentMetaMode

parse-edid < laptop_lcd_edid.bin

parse-edid < external_dell_lcd_edid.bin

```
Where the bin files are the ones you acquire for each monitor.

Also, could you tell us exact model of your external monitor?

Regards.

---

### Post by snaysler on 2016-08-03
> **papibe said:**
> Thanks.

Since you are already using the Nvidia driver, you should try to setup your monitor using 'Nvidia X Server Settings', not 'Displays'.

If that does not work, let's try to get more information. Please install this package:
```
sudo apt-get install read-edid
```
Then using the method described [here]("http://nvidia.custhelp.com/app/answers/detail/a_id/3571/~/managing-a-display-edid-on-linux") obtain the 2 EDIDs from each monitors (note that they are binary files). Then please run these commands and post back the results:
```
nvidia-settings -q CurrentMetaMode

parse-edid < laptop_lcd_edid.bin

parse-edid < external_dell_lcd_edid.bin

```
Where the bin files are the ones you acquire for each monitor.

Also, could you tell us exact model of your external monitor?

Regards.

```

snaysler@tayler-ubuntu:~$ nvidia-settings -q CurrentMetaMode


  Attribute 'CurrentMetaMode' (tayler-ubuntu:0.0): id=50, switchable=no, source=RandR :: DPY-1:
  nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}, DPY-0:
  nvidia-auto-select @1920x1080 +1920+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}


snaysler@tayler-ubuntu:~$ parse-edid < laptop_lcd_edid.bin
Checksum Correct


Section "Monitor"
	Identifier " 
                     @"
	ModelName " 
                    @"
	VendorName "LGD"
	# Monitor Manufactured week 0 of 2014
	# EDID version 1.4
	# Digital Display
	DisplaySize 380 210
	Gamma 2.20
	Option "DPMS" "false"
	Modeline 	"Mode 0" 138.00 1920 1968 2000 2070 1080 1083 1088 1111 +hsync -vsync 
EndSection
snaysler@tayler-ubuntu:~$ parse-edid < external_dell_lcd_edid.bin
Checksum Correct


Section "Monitor"
	Identifier "DELL U2713HM"
	ModelName "DELL U2713HM"
	VendorName "DEL"
	# Monitor Manufactured week 31 of 2013
	# EDID version 1.3
	# Digital Display
	DisplaySize 600 340
	Gamma 2.20
	Option "DPMS" "true"
	Horizsync 30-81
	VertRefresh 56-76
	# Maximum pixel clock is 170MHz
	#Not giving standard mode: 1280x800, 60Hz
	#Not giving standard mode: 1680x1050, 60Hz
	#Not giving standard mode: 1152x864, 75Hz
	#Not giving standard mode: 1600x1200, 60Hz
	#Not giving standard mode: 1280x1024, 60Hz


	#Extension block found. Parsing...
	Modeline 	"Mode 17" 148.50 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync 
	Modeline 	"Mode 0" 148.50 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync 
	Modeline 	"Mode 1" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 2" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
	Modeline 	"Mode 3" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
	Modeline 	"Mode 4" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
	Modeline 	"Mode 5" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
	Modeline 	"Mode 6" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
	Modeline 	"Mode 7" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
	Modeline 	"Mode 8" 25.200 640 656 752 800 480 490 492 525 -hsync -vsync
	Modeline 	"Mode 9" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
	Modeline 	"Mode 10" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
	Modeline 	"Mode 11" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
	Modeline 	"Mode 12" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
	Modeline 	"Mode 13" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
	Modeline 	"Mode 14" 74.250 1920 2448 2492 2640 1080 1082 1089 1125 +hsync +vsync interlace
	Modeline 	"Mode 15" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 16" 74.250 1920 2558 2602 2750 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 18" 74.25 1920 2008 2052 2200 540 542 547 562 +hsync +vsync interlace
	Modeline 	"Mode 19" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync 
	Modeline 	"Mode 20" 27.00 720 736 798 858 480 489 495 525 -hsync -vsync 
	Option "PreferredMode" "Mode 17"
EndSection

```

The model is in that output, but here's a link to the product on amazon:
[https://www.amazon.com/Dell-U2713HM-27-Inch-Discontinued-Manufacturer/dp/B009H0XQQY](https://www.amazon.com/Dell-U2713HM-27-Inch-Discontinued-Manufacturer/dp/B009H0XQQY)

---

### Post by papibe on 2016-08-03
Thanks.

Unfortunately, it looks like it only support 1080p over HDMI (from the [customer reviews]("https://www.amazon.com/Dell-U2713HM-27-Inch-Discontinued-Manufacturer/product-reviews/B009H0XQQY/ref=cm_cr_othr_d_viewopt_kywd?ie=UTF8&showViewpoints=1&sortBy=helpful&pageNumber=1&filterByKeyword=resolution")).

I'm not familiar with it, but it seems you would need to connecting using Mini/DisplayPort in order to get the full resolution. Does your laptop support it?

Best Regards.

---

