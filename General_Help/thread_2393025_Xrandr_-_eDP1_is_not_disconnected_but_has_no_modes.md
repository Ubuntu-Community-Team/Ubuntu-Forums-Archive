---
title: "Xrandr - eDP1 is not disconnected but has no modes"
date: 2018-05-28
forum: General Help
---

### Post by jorgeboscan on 2018-05-28
Hello.

I have installed ubuntu 18.04 on a dell inspiron 14 3000 series laptop (Intel HD graphics card).
To install ubuntu I had to add nomodeset to grub so my main display showed. After I installed, i plugged an external monitor to the hdmi port, and it works fine. The problem is I can't make the laptops screen work. It appears as if the screen is off because there's no backlight.
xrandr is giving me the following result:

xrandr: Output eDP1 is not disconnected but has no modes
Screen 0: minimum 8 x 8, current 1280 x 1024, maximum 32767 x 32767
eDP1 connected (normal left inverted right x axis y axis)
HDMI1 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024     60.02*+  75.02  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   832x624       74.55  
   800x600       75.00    60.32  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

I tried adding the screen native resolution (1366x768) following some guidelines on the forum. But it didn't work. The screen showed on ubuntu's display settings but I couldn't make it turn on.

With nomodeset, the external display is not found with xrandr, the same if I upgrade the kernel to the latest one (doesn't require nomodeset to make the embedded display work)

---

### Post by spartan7 on 2018-05-29
any luck with this ? I am also having this issue once I ran the last upgrade on ubuntu 18.04 xfce version.

---

### Post by spartan7 on 2018-05-29
I tried this command on xrandr for my 1440 screen, then went to Displays app and enabled the screen and it works. Hope this helps. 

[COLOR=#24292E][FONT=SFMono-Regular]xrandr --addmode DVI-I-1-1 1920x1200[/FONT][/COLOR]

---

