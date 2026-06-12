---
title: "Dual Monitor Issues"
date: 2017-08-20
forum: General Help
---

### Post by treymer0 on 2017-08-20
First post here, my apologies if I am violating any forum rules, but I need quick help.

I just dual booted my windows desktop with Ubuntu 16.04.3 LTS via USB install. My issue is as follows.

When Ubuntu starts up it thinks my Dell monitor is my Acer monitor and vice versa. Whenever I open settings on my Dell monitor, it shows up on my Acer monitor, but when I click on anything in settings it doesn't do anything. But, when I start clicking on my Dell monitor I am able to select settings when the actual settings menu is on my Acer monitor.

I have played around with Display settings and I have been able to get the settings to where I want them, but then when I restart my PC the settings reset resulting in the above problem again. 

My PC has a Nvidia GTX 1050ti. My main monitor is my Acer monitor which is plugged into my 1050ti via HDMI and my Dell monitor is plugged into my 1050ti as well via DVI. xrandr is aware of this:

$ xrandr --listmonitors 
Monitors: 2
 0: +*HDMI-1 1920/509x1080/286+0+0  HDMI-1
 1: +DVI-D-1 1920/509x1080/286+1920+0  DVI-D-1

Am I missing a driver or something? Is this a known issue? I greatly appreciate any help as I need this environment for school.

NOTE: My Linux experience is basic, but I can navigate myself through directories and make changes if needed.

---

### Post by treymer0 on 2017-08-20
WIP: Found the Additional Drivers tab under Software & Updates, switching to the NVIDIA binary driver to see if that helps.

---

### Post by deadflowr on 2017-08-20
Note that when you install the nvidia drivers, after you reboot it should also install an nvidia-centric settings manager which you can then use to set the display.
(usually something like nvidia xserver settings, just search for it in the dash menu; ie, press the windows key (often called the super key, i call it the windows key since it usually has the windows logo on it) on the keyboard and search nvidia, it should bring up the settings app, then simply click it to open)

---

### Post by treymer0 on 2017-08-20
Awesome! This worked perfectly and I am no longer having issues with my monitors. 

Root Cause: Missing NVIDIA Binary Driver

Solution: Switch to/install NVIDIA Binary Driver in Software & Updates >> Additional Drivers >> Under NVIDIA Corporation Select "Using NVIDIA binary driver" >> Apply Changes. Wait for install, reboot, and then you can adjust settings using NVIDIA X Server Settings

Thanks for the help. I will switch this thread to resolved.

Cheers!

---

