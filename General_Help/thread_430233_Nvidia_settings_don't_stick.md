---
title: "Nvidia settings don't stick"
date: 2007-05-01
forum: General Help
---

### Post by feffer on 2007-05-01
Just upgraded to Feisty. The nvidia driver is now 1.0-9631. The resolution setting defaults to 43 Hz (interlace). Of course, this gives a very poor monitor display with horizontal lines. Using the Nvidia Settings gui, I can change to 85 Hz and it looks great. I saved these settings to xorg.conf, but after rebooting, the display reverts back to 43 Hz. Is there a way to get my settings to stick at 85 Hz? If not, can I back down to the earlier nvidia driver, I think it was 1.0-8776?

Thanks,
feffer

---

### Post by dcstar on 2007-05-01
> **feffer said:**
> Just upgraded to Feisty. The nvidia driver is now 1.0-9631. The resolution setting defaults to 43 Hz (interlace). Of course, this gives a very poor monitor display with horizontal lines. Using the Nvidia Settings gui, I can change to 85 Hz and it looks great. I saved these settings to xorg.conf, but after rebooting, the display reverts back to 43 Hz. Is there a way to get my settings to stick at 85 Hz? If not, can I back down to the earlier nvidia driver, I think it was 1.0-8776?

Thanks,
feffer

System-Preferences-Screen Resolution

---

### Post by bodhi.zazen on 2007-05-02
> **feffer said:**
> Just upgraded to Feisty. The nvidia driver is now 1.0-9631. The resolution setting defaults to 43 Hz (interlace). Of course, this gives a very poor monitor display with horizontal lines. Using the Nvidia Settings gui, I can change to 85 Hz and it looks great. I saved these settings to xorg.conf, but after rebooting, the display reverts back to 43 Hz. Is there a way to get my settings to stick at 85 Hz? If not, can I back down to the earlier nvidia driver, I think it was 1.0-8776?

Thanks,
feffer

:lolflag: NO ! No need to downgrade your nvidia driver :)

The problem : /etc/X11/xorg.conf is a system file, so you can not save your changes when you run nvidia-settings as a user.

**Solution : Run nvidia settings as root**.

```
gksudo nvidia-settings
```

set then save your setting ...

viola

---

### Post by feffer on 2007-05-02
```
gksudo nvidia-settings
```
This seemed to work, but did not survive rebooting. I checked xorg.conf before and after reboot, and the desired resolution-refresh rate "1024x768-85" was available, but the display had interlacing after reboot.

My Nvidia card is G-force4 which is about 4-5 years old. The reason I'm suspicious is that going to System-settings-display/monitor gives me weird refresh rates ranging from 51 to 59. There is no option for 85 Hz. 

As I mentioned in my first post, the older nvidia driver 1-0.8776 didn't give me any problems. Refresh rate of 85 was available under both the nvidia-settings and system-settings-display. 

Bottom line, I still can't get my settings to persist through rebooting. Any clues?

Thanks,
feffer

---

### Post by cmon on 2007-05-05
> **feffer said:**
> ```
gksudo nvidia-settings
```
This seemed to work, but did not survive rebooting. I checked xorg.conf before and after reboot, and the desired resolution-refresh rate "1024x768-85" was available, but the display had interlacing after reboot.

My Nvidia card is G-force4 which is about 4-5 years old. The reason I'm suspicious is that going to System-settings-display/monitor gives me weird refresh rates ranging from 51 to 59. There is no option for 85 Hz. 

As I mentioned in my first post, the older nvidia driver 1-0.8776 didn't give me any problems. Refresh rate of 85 was available under both the nvidia-settings and system-settings-display. 

Bottom line, I still can't get my settings to persist through rebooting. Any clues?

Thanks,
feffer

Hi
I had the same problem as you but after I followed this guide [http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2](http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2)  my settings became rock solid.

If you walk through all steps in the guide without any errors you should be able to use Ubuntus own screen resolution tool to change your settings.

---

### Post by nikkkko on 2007-05-05
Hi,

I have the same graphics (GeForce4 MX Generic), and have just installed the same driver, 1.0-9631 and have a similar problem. In my case nvidia-settings shows my display to be CRT whereas in fact it is LCD.  At the login screen - i.e., after the driver has loaded and I have seen the nvidia logo flash on screen - I see everything pin sharp.  Once I hit return to log in, everything blurs slightly.  There is nowhere to change this in nvidia-settings as the setting to automatically determine my display simply decides it is CRT and cannot be manually altered.

?!

---

### Post by feffer on 2007-05-11
After much trial and error, this issue finally got resolved! Upgrading to Feisty brought in the Nvidia 1.0-9631 driver, but as mentioned earlier, I couldn't get refresh rates to stick through reboot. 

Based on cmon's post, I checked [http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2](http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2) and in the Problems section saw info based on my Nvidia GeForce4 420 card. The following code inserted into xorg.conf did the trick:
```
Option "ExactModeTimingsDVI" 
Option "UseEdidDpi" "FALSE" 
Option "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"
```

My gut tells me that -- Option "UseEdidDpi" "FALSE" -- is the key, but I haven't tested it yet. Here's what I think is happening. There is a conflict between parameters that the Nvidia driver allows, like 75 or 85 refresh rates, and those allowed by the kde display manager. As reported earlier, when I checked System-settings -- Display, the only refresh rates allowed there were in the range of 51-59. When I boot the machine, the resolution looks great (splash screen and session manager) until I actually log in and start kde. Once kde is started, the display interlacing starts. Anyway, this is my experience. I'd like to hear back from anyone who really knows what's going on here.

Thanks, for everyone's help. 

Regards,
feffer

---

### Post by sdil on 2007-05-12
I thinks, you just logon to this : [www.albertomilone.com/nvidia_scripts1.html](www.albertomilone.com/nvidia_scripts1.html) and read the instruction

---

### Post by KhaaL on 2007-06-08
> **feffer said:**
> After much trial and error, this issue finally got resolved! Upgrading to Feisty brought in the Nvidia 1.0-9631 driver, but as mentioned earlier, I couldn't get refresh rates to stick through reboot. 

Based on cmon's post, I checked [http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2](http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2) and in the Problems section saw info based on my Nvidia GeForce4 420 card. The following code inserted into xorg.conf did the trick:
```
Option "ExactModeTimingsDVI" 
Option "UseEdidDpi" "FALSE" 
Option "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"
```

My gut tells me that -- Option "UseEdidDpi" "FALSE" -- is the key, but I haven't tested it yet. Here's what I think is happening. There is a conflict between parameters that the Nvidia driver allows, like 75 or 85 refresh rates, and those allowed by the kde display manager. As reported earlier, when I checked System-settings -- Display, the only refresh rates allowed there were in the range of 51-59. When I boot the machine, the resolution looks great (splash screen and session manager) until I actually log in and start kde. Once kde is started, the display interlacing starts. Anyway, this is my experience. I'd like to hear back from anyone who really knows what's going on here.

Thanks, for everyone's help. 

Regards,
feffer

Your trick made my day, kudos to you! :D

---

### Post by oliwally on 2007-07-07
I'm still not having any luck with any of these suggestions. Refresh rate still needs to be manually changed after login and it just won't stick, even when changing it using sudo etc.

Any other suggestions?

---

### Post by tobinlam on 2007-10-31
I would love to have an answer.  My CRT keeps defaulting to 1280x960 but can only do 60Hz at that resolution.  It is killing my eyes!

---

### Post by Nemno on 2007-12-24
Thanx for the info,

I got it working now and after some fiddling around this is what's left in xorg.conf;

at the 'Screen Section'
    Option         "ModeValidation" "NoVesaModes"

at the 'Monitor Section'
 Modeline "1600x1200"   229.5   1600 1664 1856 2160   1200 1201 1204 1250  +hsync +vsync


I need the Modeline to make it work (this will override the edid stuf?)
The Modeline can be generated at [http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html](http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html).
I used VESA mode 1600x1200@85Hz.
Be carefull with the modeline (it can break your monitor!?) so only use settings your
monitor can handle :-k.

The weird part is that i removed the Edid lines from my xorg.conf:

    Option         "UseEdidDpi" "false"
    Option         "UseEdidFreqs" "false"


I also removed ModeValidation "NoEdidDFPMaxSizeCheck" part. And it Still works.

nvidia-settings -q refreshrate
 Attribute 'RefreshRate' (teknode:0.0; display device: CRT-1): 85.00 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

confirmed by my monitor OSD menu.
\\:D/

Thats all folks
Nemno

---

### Post by Nemno on 2007-12-28
Oh don't forget to also set your Screen Resolution via the gnome menu
System->Preferences->Screen Resolution

---

