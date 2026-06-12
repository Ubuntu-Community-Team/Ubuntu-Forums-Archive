---
title: "External monitor flashing"
date: 2016-08-25
forum: General Help
---

### Post by sotires on 2016-08-25
Hello,
Since I upgraded my laptop to Ubuntu 16,04, it flashes when I connect an external monitor, making it completely unusable. 
It also did this with Ubuntu 15.10 but not with the earlier versions, which all worked perfectly. 
I tried several different resolution settings, but it made no difference. 

Now I have connected my laptop to my wife's monitor. And surprise, it works perfectly. 
Anybody have any idea what's going on here? And how to get it to work with my monitor. 

My wife's monitor is an elderly 19 inch 1280 x 1024, whereas mine is a much bigger one, up to 1920 x 1200. But as I said, it worked with earlier versions of Ubuntu and I have tried losts of different resolution settings. 
Thanks. 
.

---

### Post by T2uiYKb7 on 2016-08-25
Can you try resetting the monitor it's self back to default using the physical keys on the monitor?

If there are overdrive or refresh rate settings (on the monitor) can you try changing those?

Does it flash too much to use at all? If not can you type **xrandr** in the terminal and paste the results?

---

### Post by sotires on 2016-08-26
Hello
   Here is the result from xrandr using my wife&#8217;s monitor
 
 
 sotires@sotires-ThinkPad-X200:~$ xrandr
 Screen 0: minimum 8 x 8, current 1996 x 1824, maximum 32767 x 32767
 LVDS1 connected primary 1280x800+0+1024 (normal left inverted right x axis y axis) 261mm x 163mm
    1280x800      60.00*+  50.00   
    1024x768      60.00   
    800x600       60.32    56.25   
    640x480       59.94   
    640x400       60.00   
 DP1 disconnected (normal left inverted right x axis y axis)
 DP2 disconnected (normal left inverted right x axis y axis)
 DP3 disconnected (normal left inverted right x axis y axis)
 HDMI1 disconnected (normal left inverted right x axis y axis)
 HDMI2 disconnected (normal left inverted right x axis y axis)
 VGA1 connected 1280x1024+716+0 (normal left inverted right x axis y axis) 376mm x 301mm
    1280x1024     60.02*+  75.02   
    1152x864      75.00   
    1024x768      75.08    75.03    60.00   
    832x624       74.55   
    800x600       75.00    60.32   
    640x480       75.00    60.00   
    720x400       70.08   
 VIRTUAL1 disconnected (normal left inverted right x axis y axis)
 
 
 Here is the result from xrandr on my monitor, before changing settings
 xrandr
 Screen 0: minimum 8 x 8, current 1280 x 1568, maximum 32767 x 32767
 LVDS1 connected primary 1280x800+0+768 (normal left inverted right x axis y axis) 261mm x 163mm
    1280x800      60.00*+  50.00   
    1024x768      60.00   
    800x600       60.32    56.25   
    640x480       59.94   
    640x400       60.00   
 DP1 disconnected (normal left inverted right x axis y axis)
 DP2 disconnected (normal left inverted right x axis y axis)
 DP3 disconnected (normal left inverted right x axis y axis)
 HDMI1 disconnected (normal left inverted right x axis y axis)
 HDMI2 disconnected (normal left inverted right x axis y axis)
 VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
    1024x768      60.00*  
    800x600       60.32    56.25   
    848x480       60.00   
    640x480       59.94   
 VIRTUAL1 disconnected (normal left inverted right x axis y axis)
 sotires@sotires-ThinkPad-X200:~$

---

### Post by sotires on 2016-10-01
Sorted. It turns out to have been a monitor hardware problem. 

I installed an old version of Ubuntu on a spare hard disc and found that I was getting exactly the same symptoms. 
So it's not related to the upgrade. Then I tried the monitor on every available computer (Win7, win 10, TV streaming box etc) and got the same symptoms, on devices that it had worked with before. 
Then, a thump on the side of the monitor and the symptoms cleared. Proving conclusively that the problem was with the monitor hardware, not software drivers, settings, video output, and every other red herring I have tried over the past year. 
Dealing with intermittent faults was always a problem in the days of tube TVs, with their high temperature and high voltage environment. 
I guess I'll open up the monitor and fish out the can of freezer spray when I get some time. But at least I've stopped looking in the wrong place.

---

