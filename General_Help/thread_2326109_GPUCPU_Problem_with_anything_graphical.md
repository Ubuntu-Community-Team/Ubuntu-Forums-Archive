---
title: "GPU/CPU Problem with anything graphical"
date: 2016-05-28
forum: General Help
---

### Post by 1two3 on 2016-05-28
[h=2]Laptop specs[/h]

[LIST]
[*]Acer Aspire V3-571G
[*]Intel Core i5-3230M 2.6GHz (3.2GHz)
[*]NVIDIA GeForce GT 630M with 1GB Dedicated VRAM
[*]8GB DDR3 Memory
[*]500GB HDD
[/LIST]

[U]
This is what **inxi -b** shows for **graphics**:[/U]

Card-1: Intel 3rd Gen Core processor Graphics Controller
Card-2: NVIDIA GF108M [GeForce GT 630M]
Display Server: X.Org 1.18.3 driver: nvidia
Resolution: 1920x1080@59.97hz
GLX Renderer: GeForce GT 630M/PCIe/SSE2
GLX Version: 4.5.0 NVIDIA 361.42


**I've installed Ubuntu on Legacy BIOS mode**.


One day I decided to install Ubuntu Desktop 14.04 64bit LTS and I also 
installed LVM with disk encryption and I overwrote Windows so there was 
no dual boot. I had this same problem on that Ubuntu install.

Then I reinstalled Ubuntu but this time **without** LVM and
 disk encryption and instead of 14.04 I installed 16.04. The problem 
remained. I made a post here asking for help and towards at the end of 
the 70ish comment chain I reinstalled Ubuntu Desktop 16.04 64bit LTS so 
that **I'm currently running a clean install of Ubuntu** except that I've switched 
to using **NVIDIA binary driver - version 361.42 from nvidia-361 (proprietary, tested)** 
and I've checked nvidia settings that Nvidia prime is using my nvidia card.


Problem:
If I play a game such as Dota2 or Team Fortress 2 which are games that support Linux then it's super lagging and unplayable. 
If I watch videos on youtube or any other website then after a few minutes it will very often start lagging a lot so I need to pause 
the video and wait a while before resuming it. Same problem when watching videos that I've downloaded by using VLC. I can also start lagging a lot just 
from having two facebook photo galleries open oftentimes. 


glxinfo | head -n 50[/h]  name of display: :0
 ```
 display: :0  screen: 0
  direct rendering: Yes
  server glx vendor string: NVIDIA Corporation
  server glx version string: 1.4
  server glx extensions:
  GLX_ARB_context_flush_control, GLX_ARB_create_context,   GLX_ARB_create_context_profile, GLX_ARB_create_context_robustness,   GLX_ARB_fbconfig_float, GLX_ARB_multisample, GLX_EXT_buffer_age,   GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile,   GLX_EXT_framebuffer_sRGB, GLX_EXT_stereo_tree, GLX_EXT_swap_control,   GLX_EXT_swap_control_tear, GLX_EXT_texture_from_pixmap,   GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_NV_copy_image,   GLX_NV_delay_before_swap, GLX_NV_float_buffer,   GLX_NV_multisample_coverage, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,   GLX_SGI_swap_control, GLX_SGI_video_sync   client glx vendor string: NVIDIA Corporation
  client glx version string: 1.4
  client glx extensions:
  GLX_ARB_context_flush_control, GLX_ARB_create_context,   GLX_ARB_create_context_profile, GLX_ARB_create_context_robustness,   GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address, GLX_ARB_multisample,   GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile,   GLX_EXT_create_context_es_profile, GLX_EXT_fbconfig_packed_float,   GLX_EXT_framebuffer_sRGB, GLX_EXT_import_context, GLX_EXT_stereo_tree,   GLX_EXT_swap_control, GLX_EXT_swap_control_tear,   GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating,   GLX_NV_copy_buffer, GLX_NV_copy_image, GLX_NV_delay_before_swap,   GLX_NV_float_buffer, GLX_NV_multisample_coverage, GLX_NV_present_video,   GLX_NV_swap_group, GLX_NV_video_capture, GLX_NV_video_out,   GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_swap_control,   GLX_SGI_video_sync   GLX version: 1.4
  GLX extensions:
  GLX_ARB_context_flush_control, GLX_ARB_create_context,   GLX_ARB_create_context_profile, GLX_ARB_create_context_robustness,   GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address, GLX_ARB_multisample,   GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile,   GLX_EXT_create_context_es_profile, GLX_EXT_framebuffer_sRGB,   GLX_EXT_stereo_tree, GLX_EXT_swap_control, GLX_EXT_swap_control_tear,   GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating,   GLX_NV_copy_image, GLX_NV_delay_before_swap, GLX_NV_float_buffer,   GLX_NV_multisample_coverage, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,   GLX_SGI_swap_control, GLX_SGI_video_sync   OpenGL vendor string: NVIDIA Corporation
  OpenGL renderer string: GeForce GT 630M/PCIe/SSE2
  OpenGL core profile version string: 4.5.0 NVIDIA 361.42
  OpenGL core profile shading language version string: 4.50 NVIDIA
  OpenGL core profile context flags: (none)
  OpenGL core profile profile mask: core profile
```

[SIZE=7][SIZE=4]
[/SIZE]
[/SIZE]

---

### Post by wildmanne39 on 2016-05-28
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by 1two3 on 2016-05-28
Thanks, Wild Man, I will remember that for the next time :)

---

### Post by ajgreeny on 2016-05-28
And please use standard font size.  Huge fonts such as you used do not bring answers any quicker; in fact they may put some people off entirely.

---

### Post by 1two3 on 2016-05-28
Really? I thought it was standard to use a larger font size for section headings so that it's easier to scan through the post.

---

### Post by ajgreeny on 2016-05-28
> **1two3 said:**
> Really? I thought it was standard to use a larger font size for section headings so that it's easier to scan through the post.
Not in this forum!
By all means use bold for headings or to emphasize a few words in colour fi you wish, but a whole large font section as you used, or in upper case, which I accept you didn't use, is commonly **[SIZE=4]known as shouting[/SIZE]** and therefore is frowned on here.

---

### Post by $yl9pAR%t on 2016-05-28
Hi again! No happy end last time. This thread looks slightly different to the previous one. I will try to not disturb, but could you check what is going on with your CPU and temperature when your Ubuntu is getting sluggish?

1. Use lm-sensors to check temperatures before you start using youtube and later when youtube will start lagging.

2. Use htop to check CPU usage when youtube is in use, especially the moment when youtube will start lagging.

---

### Post by 1two3 on 2016-05-29
Okay, **sensors** before youtube: 

```
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +68.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +68.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +68.0°C  (high = +87.0°C, crit = +105.0°C)
```


Started Youtube: 
```
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +76.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +75.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +72.0°C  (high = +87.0°C, crit = +105.0°C)
```


Started lagging: 
```
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +87.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +85.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +83.0°C  (high = +87.0°C, crit = +105.0°C)
```


And a screenshot of **htop** during lagging (removed my username for privacy): 
[ATTACH=CONFIG]269348[/ATTACH]

---

### Post by $yl9pAR%t on 2016-05-30
I have to give up. I do not understand this crazy CPU usage when playing just Youtube. Do you have the same with Intel GPU enabled?

BTW:
Your uptime is over 6 days, is your laptop always on?

---

### Post by mastablasta on 2016-05-31
high CPU usage is indicating it is doing the software acceleration. looks like hardware acceleration is not working.

what happens if you run any of the phoronix test from their test suite? does the PC even pass them well?

---

### Post by 1two3 on 2016-05-31
It's the same with Intel GPU enabled and yes, I don't turn my computer off, only reboot when necassary. 
I don't see any reason to turn off the computer at night.


Can  you tell me briefly what phoronix test suite is? I searched for it but  found only installation instructions for Ubuntu 11 and those really old  versions.. can I use those old installation instructions for 16.04?


There's  one thing I left out in this post because I mentioned it in a past  thread I had made but no one thought it was a problem, so it probably  isn't but I just want to add that piece of info here just to make sure I  have left absolutely no information that could help figure out what's  wrong. 


It's just so strange.. It's after all pretty much a clean install of Ubuntu Desktop 16.04 64bit LTS.. and it's not working.
If  I would in the future buy a new computer that I would want Ubuntu on,  how can I avoid this from happening to that computer as well? Is it just  a gamble? 
Is this about compatibility?


Edit: forgot to actually mention that missing info bit (lol)...
In **Software & Updates > Addition Drivers** it says there's an **Unknown: Unknown** device and that **"This device is not working."** 
It gives me two options: 

1. Using Processor microcode firmware for Intel CPUs from intel-microcode (proprietary)
2. Do not use the device

And it's currently not using the device.


Edit 2: I also notice that I forgot to mention it in the first post of this thread but this computer works great with Windows.. I get no lag, no CPU problem and can play games on high settings.. have many youtube tabs open simultanously and  so on.

---

### Post by 1two3 on 2016-06-01
I don't have a good reason really for not having tried the Processor microcode proprietary driver for the unknown device yet. 
It's really just because in the past thread no one thought this could be the reason for the problem I'm having plus I didn't know what could happen if I chose to use an unknown device that says that it's not working. But I misunderstood that "is not working" message. I thought it was because there's something wrong with it but it's simply because by default after installing Ubuntu, it wasn't using the device so of course it isn't working :) 


But as my absolute last option I went ahead with trying to use that device then rebooted the computer but it didn't fix anything.

---

