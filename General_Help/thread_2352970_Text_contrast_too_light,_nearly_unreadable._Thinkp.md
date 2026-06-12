---
title: "Text contrast too light, nearly unreadable. Thinkpad T410"
date: 2017-02-17
forum: General Help
---

### Post by Jack_Dickerson on 2017-02-17
Text contrast too light, nearly unreadable. Occurs system-wide, but especially in browsers.
Lenovo Thinkpad t410.   Ubuntu-Mate 16.04. 
I can't find a solution anywhere. Can anyone help?
Thanks
JackD

---

### Post by DuckHook on 2017-02-17
Try choosing a different theme by right clicking anywhere on the desktop&#8594;Change Desktop Background&#8594;Theme&#8594;<then, select another theme>

Though unlikely, you may also have a colour-depth issue. Please post output of:```
xwininfo -root | grep -i depth
```

Which driver are you using? Please provide HW specs.

---

### Post by Jack_Dickerson on 2017-02-19
I hope this is the info you want.  I hope it's enough. I apologize if it's too much.
MATE Desktop Environment 1.12.1.  Also I've tried changing themes- no difference.  

```
-$ xwininfo -root | grep -i depth
  Depth: 24
```

lspci
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02

-Display-
Resolution        : 1440x900 pixels
Vendor        : The X.Org Foundation
Version        : 1.18.4
-Monitors-
Monitor 0        : 1440x900 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
Present
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
XVideo-MotionCompensation
-OpenGL-
Vendor        : Intel Open Source Technology Center
Renderer        : Mesa DRI Intel(R) Ironlake Mobile 
Version        : 2.1 Mesa 11.2.0
Direct Rendering        : Yes
```

Here's a couple of screenshots.
 [IMG][[IMG]http://www.zimagez.com/miniature/screenshotat2017-02-17093525.png[/IMG]]("http://www.zimagez.com/zimage/screenshotat2017-02-17093525.php")[/IMG][IMG][[IMG]http://www.zimagez.com/miniature/screenshotat2017-02-19113325.png[/IMG]]("http://www.zimagez.com/zimage/screenshotat2017-02-19113325.php")[/IMG]


Again, Thank you both very much.

---

### Post by DuckHook on 2017-02-19
Please post output of:```
xrandr
```...and post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by vasa1 on 2017-02-19
Hi,

Could you please use the paper-clip icon to upload images? At least for me, the zimagez images are too small :( and the "enlarge" icon does nothing for me.

BTW, there's a trend to use light grey text on a white background. Apparently, people who make decisions re. the "user experience" feel it's elegant or something.

---

### Post by Jack_Dickerson on 2017-02-20
Thanks for your reply.  Here is the output to :~$ xrandr:
```

Screen 0: minimum 8 x 8, current 1440 x 900, maximum 32767 x 32767
LVDS1 connected primary 1440x900+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1440x900      60.06*+  59.89    49.30  
   1360x768      59.80    59.96  
   1280x800      60.00  
   1152x864      60.00  
   1024x768      60.00  
   800x600       60.32    56.25  
   720x450       60.00  
   640x480       59.94  
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by DuckHook on 2017-02-21
Please open a terminal and execute the following:```
xrandr --output LVDS1 --set "Broadcast RGB" "Full"
```If xrandr returns an error saying there is no such display, then change the "1" to a "0" and try again```
xrandr --output LVDS0 --set "Broadcast RGB" "Full"
```

Does this make a difference?

---

