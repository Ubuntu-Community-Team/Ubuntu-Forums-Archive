---
title: "Load x / GUI when screen is turned off LUbuntu 15.04 (start monitor later)"
date: 2015-08-08
forum: General Help
---

### Post by axel12 on 2015-08-08
Hi! I would like to load (boot up) ubuntu completely without turning the monitor on.
Running Lubuntu 15.04. 

I want to start ubuntu fully. And then after the boot is ready (GUI and applications are loaded)
i want to turn on my monitor.

Now it works like this: I start my pc and it halts the boot just before GUI loads, I have set up auto login so as soon as i start my screen the mouse courser shows 
and GUI appears. But if i dont start my screen my pc doesnt load or boot up. 

Quite new to linux, when i had Windows this worked just fine. pls dont force me to go back..have been struggling with this for days
Need to load my monitor after pc is ready

[http://askubuntu.com/questions/166009/use-ubuntu-graphical-desktop-without-monitor-at-boot](http://askubuntu.com/questions/166009/use-ubuntu-graphical-desktop-without-monitor-at-boot)
[http://ubuntuforums.org/showthread.php?t=1466271](http://ubuntuforums.org/showthread.php?t=1466271)

---

### Post by axel12 on 2015-08-08
Finally! Found a solution  forget about disable KMS , Option       "IgnoreEDID" , vesa driver or xconf driver dummy or hardw dummy.

[https://markbrewster.wordpress.com/2010/02/04/ubuntu-9-10-not-starting-up-at-full-resolution-with-tv-turned-off/](https://markbrewster.wordpress.com/2010/02/04/ubuntu-9-10-not-starting-up-at-full-resolution-with-tv-turned-off/) 

1. Forced xorg.conf from Nvidia settings (specified resolution , frec) + look up DFP-[B]X
[/B]2. Nvidia setting Acquire EDID , save file 
3. xorg.conf Under Section device add. file path + DFP-[B]X
[/B]       Option &#8220;CustomEDID&#8221; &#8220;DFP-0:/home/mark/Desktop/edid.bin&#8221; &#8216;DFP-0&#8242;
4. under the &#8216;Section &#8220;Screen&#8221;&#8216;:
Option         "ConnectedMonitor" "DFP-0"
(This forces the graphics card to assume the above monitor is connected)
Option         "metamodes" "DFP-0: 1920x1080_60i +0+0"
(This line had lots more modes specified, separated by commas and semicolons).

Thnaks Mark Brewster's Blog

---

