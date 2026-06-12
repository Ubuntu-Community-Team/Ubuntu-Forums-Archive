---
title: "How can I fix the aspect ratio?"
date: 2013-11-07
forum: General Help
---

### Post by osakawilson2 on 2013-11-07
My computer is hooked up to my Panasonic Wide-Screen TV and I use it as a media center (using Ubuntu 13.04 without a specialized media center app.)

Processor: Intel Core i7-3770 CPU@3.40GHz x 8. 
Graphics: Intel Ivybridge Desktop x86/MMX/SSE2
OS: Ubuntu 13.04 32-bit
Monitor: Panasonic TH-37PD10 (BS-110°CS Digital)

The TV/monitor is specs say list it as 852×480, but only the options in  the Display Settings are 1024X768 (4:3) and 800X600 (4:3). I use  1024X768 because, the icons and the fonts are a good size. It fills the  full screen, but is stretched out so all of the movies, pictures, and  such, are distorted. I went to Software & Updates/Additional Drivers  and it doesn't list any alternatives that I can use. (Assuming it  would.)

Is there anything I can do to make this monitor produce non-distorted output?

I posted this to Multimedia/Video and got no replies.

---

### Post by TheFu on 2013-11-07
Take a look at **xrandr**

Here is the output on my old XBMC server (a Netbook)```

$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0*+   65.0  
   800x600        60.3     56.2  
   640x480        59.9
```

Here is the output on my newer, high-powered, AMD E350 XBMC $99 server:
```
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 720, maximum 1920 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1280x720+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       59.8 +
   1920x1080      60.0     50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1776x1000      50.0     59.9     25.0     24.0     30.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       60.0  
   1280x960       60.0  
   1366x768       59.8  
   1360x768       59.8  
   1280x768       59.8  
   1280x720       60.0*    50.0     59.9  
   1024x768      120.0     75.0     70.1     60.0  
   1152x648       50.0     59.9  
   1024x600      120.0     75.0     70.1     60.0  
   800x600       120.0     72.2     75.0     60.3     56.2  
   800x480       120.0     72.2     75.0     60.3     56.2  
   720x480        30.0     60.0     30.0     59.9  
   640x480        75.0     72.8     67.0     60.0     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)

```

Using xrandr, you can force the output to any of the **supported** modes/resolutions. Whether the display supports any one or not is a different question.  **man xrandr** explains.
On LXDE, there is the **lxrandr** tool that has a GUI and will list the modes to be selected and saved. I suspect every DE will have something similar, you just need to find it.  Which DE are you running?

---

### Post by osakawilson2 on 2013-11-07
Thanks. I will give this a try. I'm using Ubuntu 13.4.

---

### Post by TheFu on 2013-11-07
Ubuntu 13.04 is the OS (the "04" is important).  You probably are running Unity DE ... which I have never used. Someone should see this question and will be able to explain all the point-n-clicking necessary to get to the display settings.  Too much hassle for me, sorry.

Might be worth reading my LTS link in my signature above.

---

### Post by XBNCPRk on 2013-11-07
An odd question... from what I can see (and its limited because that model is only available in Japan and thats one language I never learned), that is an hd set. The 1024x768 looks to be the tvs native resolution... Why are you trying to watch it at a sd/480 resolution?

---

