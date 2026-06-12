---
title: "Unable to get 1024x768 &amp; its lower resolutions light up with Sony VPL-CH370 projector"
date: 2023-02-07
forum: General Help
---

### Post by appusony on 2023-02-07
Dear all,


1. I am unable to get my Sony VPL-CH370 ([https://pro.sony/en_BN/products/laser-projectors/vpl-ch370#ProductSpecificationsBlock-vpl-ch370](https://pro.sony/en_BN/products/laser-projectors/vpl-ch370#ProductSpecificationsBlock-vpl-ch370)) projector lighting up **with 1024x768 resolution & all its lower resolutions (1024x768, 800x600, 720x400, 640x480),** where as it lights up from 1280x720 & all its higher resolutions (from  1280x720, 1280x800, 1280x1024, 1440x900, 1600x900, 1680x1050 to 1920x1080p) till 1920x1080p which is the max resolution supported by the projector, which is connected via typeC to VGA converter, VGA port is connected towards the projector & typeC end is connected to my Ubuntu laptop with "ubuntu 22.04.1 and 5.15.0-56-generic.i5-1155G7@2.5Hz" , tried even command line using xrandr, but still unable to get it working with 1024x768 resolution & all its lower resolutions, any driver specific patches needs to be incorporated specific to Sony VPL-CH370 VGA to get this 1024x768 resolution & all its lower resolutions (1024x768, 800x600, 720x400, 640x480) working please?


2. I am wondering , may I know please, if any idea, what it the key difference between a **VGA monitor & a VGA projector**?


3. I am able to get this working when I tried to connect VGA monitor instead of Sony VPL-CH370 projector, but I am wondering, why I am unable to get this working with the projector specifically with 1024x768 resolution & all its lower resolutions (1024x768, 800x600, 720x400, 640x480)


4. all the resolutions works well with windows laptop with this specific Sony VPL-CH370 projector, my worries is please, why I am unable to get this working with the projector specifically with 1024x768 resolution & all its lower resolutions (1024x768, 800x600, 720x400, 640x480)




Any help would be much appreciated please, as I am stuck with this for quite long time.


Many thanks in advance!

---

### Post by appusony on 2023-02-10
Dear All, Any advices or inputs/pointers regarding the above please?

---

### Post by ActionParsnip on 2023-02-10
A projector is seen as a monitor in all OSes. They're treated the same

---

### Post by appusony on 2023-02-12
Thank you very much, May  I know please, any inputs or pointers on points #1, #3 and #4?

---

### Post by lessi2306 on 2023-02-12
Hello,

have you tried to manage the allowed resolutions of the projector via xrandr?

1. Get the right settings:
cvt 1024 768

2. Add the right mode with the settings from above:
xrandr --newmode  [FONT=monospace][COLOR=#000000]"1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

3. Acitivate the mode to port VGA1 (if it is the right port for your setting):
xrandr --addmode VGA1 [/COLOR][/FONT][FONT=monospace][COLOR=#000000]"1024x768_60.00"[/COLOR][/FONT]
[FONT=monospace]
Greetings,
Stefan
[/FONT]

---

