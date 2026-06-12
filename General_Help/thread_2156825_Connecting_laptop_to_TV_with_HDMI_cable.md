---
title: "Connecting laptop to TV with HDMI cable"
date: 2013-06-23
forum: General Help
---

### Post by bencouve on 2013-06-23
I need some advice on connecting my PC to the TV. I have purchated a HDMI cable, done some searches for other who have had this probem but am no further ahead.

Before I start would like to advise that I use an external monitor because the montor on my Laptop died a long time ago, don't know if that make a difference. Below I have listed some info that seems to be requested often by you guys to help speed up the process. 

Useful info
product: HP Pavilion dv6 Notebook PC (VL073EA#ABU)

[TABLE="class: node"]
[TR]
[TD="class: first"]id:
[/TD]
[TD="class: second"]display:0

[/TD]
[/TR]
                [TR]
[TD="class: first"]description: [/TD]
[TD="class: second"]VGA compatible controller[/TD]
[/TR]
              [TR]
[TD="class: first"]product: [/TD]
[TD="class: second"]Mobile 4 Series Chipset Integrated Graphics Controller[/TD]
[/TR]
              [TR]
[TD="class: first"]vendor: [/TD]
[TD="class: second"]Intel Corporation[/TD]
[/TR]
              [TR]
[TD="class: first"]physical id: [/TD]
[TD="class: second"]2

[/TD]
[/TR]
[/TABLE]

If I type xrandr I get

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 348mm x 197mm
   1366x768       59.9 +
   1280x1024      60.0  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       60.0* 
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI1 connected (normal left inverted right x axis y axis)
   1440x900       60.2 +
   1920x1080      50.0     60.0     25.0     30.0  
   1680x1050      59.9  
   1280x1024      60.0  
   1360x768       60.2  
   1280x800       59.9  
   1280x720       50.0     60.0  
   1440x576       25.0  
   1024x768       75.1     70.1     60.0  
   1440x480       30.0  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0     50.0  
   720x480        59.9     59.9  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)


This may be a driver problem because when I go to the Unity Dash and type "drivers", I don't see the "additional drivers" option that seems to appear for others. Maybe doing something wrone

Please advise. Thanks in advance.

---

### Post by SeijiSensei on 2013-06-23
Do you also have another video card on this machine? My machine has an ATI adapter as well.  Try running "lspci | grep VGA" from a terminal prompt.  On my dv6t I get

```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [Radeon HD 6730M/6770M/7690M XT]

```

I went into the BIOS and set the video adapter to "fixed mode".  This forces the machine to prefer the ATI controller.  Afterwards, I could install the proprietary ATI driver and use it to connect over the HDMI port.  The fixed-mode option was added to the firmware sometime in 2011.  If your machine has an ATI card, but no fixed-mode option in the BIOS, see [if a newer firmware release exists for your model]("http://forum.notebookreview.com/hp-drivers-software-forum/556469-drivers-hp-dv6-4xxx-dv6-6xxx-dv7-5xxx-dv7-6xxx-envy-14-2xxx-envy-17-2xxx-intel.html").

The ATI board was an upgrade; not all dv6's have one straight from the factory.

My TV also has a standard 15-pin VGA port.  I've found it easier to connect to that, and the image quality is fairly comparable to HDMI. If your TV has a VGA port, I suggest giving that a try.

---

### Post by bencouve on 2013-06-23
Hi, thanks for the response. I have done what you have said and the output is as below.

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)


So I guess I do not have ATI controller. What do I do next ?

---

### Post by bencouve on 2013-06-23
One other thing, as a subset of this command

sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

I have 

[TABLE="class: node"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"]display:0
[/TD]
[/TR]
                [TR]
[TD="class: first"]description: [/TD]
[TD="class: second"]VGA compatible controller[/TD]
[/TR]
              [TR]
[TD="class: first"]product: [/TD]
[TD="class: second"]Mobile 4 Series Chipset Integrated Graphics Controller[/TD]
[/TR]
              [TR]
[TD="class: first"]vendor: [/TD]
[TD="class: second"]Intel Corporation[/TD]
[/TR]
              [TR]
[TD="class: first"]physical id: [/TD]
[TD="class: second"]2
[/TD]
[/TR]
              [TR]
[TD="class: first"]bus info: [/TD]
[TD="class: second"]pci@0000:00:02.0
[/TD]
[/TR]
              [TR]
[TD="class: first"]version: [/TD]
[TD="class: second"]07[/TD]
[/TR]
              [TR]
[TD="class: first"]width: [/TD]
[TD="class: second"]64 bits[/TD]
[/TR]
              [TR]
[TD="class: first"]clock: [/TD]
[TD="class: second"]33MHz[/TD]
[/TR]
              [TR]
[TD="class: first"]capabilities: [/TD]
[TD="class: second"]msi pm vga_controller bus_master cap_list rom [/TD]
[/TR]
              [TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] driver[/TD]
[TD]=[/TD]
[TD]i915[/TD]
[/TR]
[TR]
[TD="class: sub-first"] latency[/TD]
[TD]=[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
              [TR]
[TD="class: first"]resources:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] irq[/TD]
[TD]:[/TD]
[TD]47[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]d0000000-d03fffff[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]c0000000-cfffffff[/TD]
[/TR]
[TR]
[TD="class: sub-first"] ioport[/TD]
[TD]:[/TD]
[TD]7110(size=8)[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
            [/TABLE]
                                              [TABLE="class: node-unclaimed"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"]display:1
[/TD]
[/TR]
                [TR]
[TD="class: first"]description: [/TD]
[TD="class: second"]Display controller[/TD]
[/TR]
              [TR]
[TD="class: first"]product: [/TD]
[TD="class: second"]Mobile 4 Series Chipset Integrated Graphics Controller[/TD]
[/TR]
              [TR]
[TD="class: first"]vendor: [/TD]
[TD="class: second"]Intel Corporation[/TD]
[/TR]
              [TR]
[TD="class: first"]physical id: [/TD]
[TD="class: second"]2.1
[/TD]
[/TR]
              [TR]
[TD="class: first"]bus info: [/TD]
[TD="class: second"]pci@0000:00:02.1
[/TD]
[/TR]
              [TR]
[TD="class: first"]version: [/TD]
[TD="class: second"]07[/TD]
[/TR]
              [TR]
[TD="class: first"]width: [/TD]
[TD="class: second"]64 bits[/TD]
[/TR]
              [TR]
[TD="class: first"]clock: [/TD]
[TD="class: second"]33MHz[/TD]
[/TR]
              [TR]
[TD="class: first"]capabilities: [/TD]
[TD="class: second"]pm bus_master cap_list [/TD]
[/TR]
              [TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] latency[/TD]
[TD]=[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
              [TR]
[TD="class: first"]resources:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]d5400000-d54fffff[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

---

### Post by SeijiSensei on 2013-06-23
So, I take it the VGA option isn't available to you?

I think even when I was using the Intel card I just controlled the display using the standard management tool in KDE's System Settings.  I do recall having a hard time trying to get both the laptop display and the TV to agree on a common resolution.  I wanted both of them to run at 1280x720, but the laptop display prefers 1366x768.

---

### Post by bencouve on 2013-06-23
Ok, thanks for your comments, it is always appreciated!

---

