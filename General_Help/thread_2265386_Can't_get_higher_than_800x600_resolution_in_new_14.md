---
title: "Can't get higher than 800x600 resolution in new 14.10/Utopic install"
date: 2015-02-14
forum: General Help
---

### Post by braniac5 on 2015-02-14
Heyo. I installed Ubuntu alongside Windows recently and my only screen resolution option is 800x600 - everything's too big, I can't adjust the size of open windows, my wallpaper's hideous, my personal life is a mess, and so forth. 

My xrandr output in terminal is: 

[SIZE=1]xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected primary 800x600+0+0 0mm x 0mm
   800x600        75.0*[/SIZE]

I've tried various solutions presented online with no luck. However, I've had TREMENDOUS luck asking for help in the forums in the past, so I figured I'd give this a try rather than chucking my laptop out the window. Any suggestions/tips/commands/demands would be welcome.

---

### Post by nerdtron on 2015-02-14
Probably some expert on graphics can help but it would be better is you add details on your computer specs or laptop model especially on graphics card model.

What does the the Additional Drivers on the system settings say? No available drivers?

---

### Post by braniac5 on 2015-02-15
The additional drivers section was the first place I went after my install and it said "no proprietary drivers in use." 

After some tinkering (and I tinkered a lot) the additional drivers section informed me that the computer was using the "AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source, tested)" and that I had the option to use "Video driver for the AMD graphics accelerators from fglrx (proprietary)" which I selected, rebooted, and now everything's coming up Milhouse. 

Thanks for the help - I legitimately wouldn't have thought to check Additional Drivers (since I'd checked it numerous times before) had I not read your response, so thanks!

---

