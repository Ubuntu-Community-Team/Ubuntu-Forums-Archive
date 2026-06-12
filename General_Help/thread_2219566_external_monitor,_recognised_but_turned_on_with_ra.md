---
title: "external monitor, recognised but turned on with random delay"
date: 2014-04-24
forum: General Help
---

### Post by herkules on 2014-04-24
Good evening!

I'm facing a really strange problem with my Dell Latitude E7440 (with touch screen) running ubuntu 14.04 related to external monitors (via docking station).

- When I'm putting it into the docking station, nothing seems to happen (external monitor remains black)
- While the monitor remains black, ubuntu still seems to recognize the external monitor
   * In system-settings -- displays, the external monitor shows up correctly (e.g. resolution options etc). 
   * the mouse can "move out of the build-in monitor and move into the other one"
   * when switching work-spaces, I can get a glimpse of the "other monitor"
- After some random time (between few seconds to minutes to never), suddenly the external monitor works and shows the desktop (without me triggering anything related to it.)

If the external monitor was working, but the system goes to standby, the same peculiar behavior ocurrs.

Does anyone have a clue what I might have to do?

Thanks a lot in advance,

Ulrich

---

### Post by coldcritter64 on 2014-04-24
Try this code in a terminal and see if the monitor is showing up

```
xrandr --query
```
Post back the results here and identify (if you can) which is the monitor not turned on. Use [noparse]```

```[/noparse] tags around your output in the editor. To do so use the "advanced" editor, copy/paste then highlight the output and click the # button on the editor's toolbar .

You may then be able to turn it on with xrandr (from a launcher later, _*if*_ the code works in terminal first) if we can get the correct identifier for the monitor.

Edit. OP your problem may be elsewhere re. "timing". I initially misread the post, but that command and the IDs may be of some use later. Cheers.

---

### Post by herkules on 2014-04-25
Hi.

Thanks for the reply!

The output of xrandr --query is
```

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 309mm x 173mm
   1920x1080      60.0*+   59.9  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0 +
   1920x1080      60.0*    50.0  
   1680x1050      60.0  
   1600x900       60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x800       59.8  
   1280x720       60.0     50.0     59.9  
   1024x768       60.0  
   800x600        60.3     56.2  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        60.0     59.9  
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```
The output is the same in both cases - with or without the external monitor working.

Maybe I can add the this laptop is actually ubuntu certified to work with 12.04. Yesterday eve I tried it with t12.04 (running from a live-usb), but the same problem ocurrs....

Thanks again!

---

### Post by coldcritter64 on 2014-04-25
> The output is the same in both casesI suspected that may have been the case (see my last edit). I was working on a misreading of your first post when asking for that code output.

I am not sure what in your system controls the connecting of the external monitor and the timing issue you're having. Wait further replies etc.. Good Luck.

---

