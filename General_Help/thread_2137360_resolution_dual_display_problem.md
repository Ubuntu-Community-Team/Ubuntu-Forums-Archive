---
title: "resolution dual display problem"
date: 2013-04-20
forum: General Help
---

### Post by eyeneedhelp on 2013-04-20
i have 2 identical 19 in samsung 914v monitors connected to a pny dual port video card.
no matter what i do they look different!
i set them up exactly the same yet one is stretched out and cuts off at the time on the right.
i cannot make them look alike??

---

### Post by eyeneedhelp on 2013-04-21
id really like to know if anybody ever had this problem. i use system settings for both exactly the same, but they look different and i cant even tweek the setting to different resolutions and do any better.??

---

### Post by ksanger on 2013-04-21
I have two Samsung 24" S24B240 monitors being driving by a Saphire AMD Radeon HD 7770 video card with Ubuntu 12.04.  To do this I needed to find and follow instructions for loading the ATI/AMD Radeon Graphics Driver.  This also installed AMD Catalyst Control Center.  From catalyst I was able to setup both displays at their correct resollution. (1920 x 1080).  Then I was able to select System Settings, Displays, and uncheck mirror displays so that each display extended my desktop.  I was also able to use AMD Catalyst Control Center to adjust the color on each monitor.  If your pny video graphics card used Radeon AMD or ATI graphics ICs you might be able to do the same.  If your card uses Nvidia or GForce then you need to find a similar software package for Nvidia.

---

### Post by eyeneedhelp on 2013-04-22
well,,,i had set them to the SAME res,but 5x4, the way i wanted them,both same, but they looked different as i said.
 but when i set to 4x3,they do indeed look alike!. all from system settings.
i guess i assumed if the res was the same they should also be?
at least i can see everything and i thank you!

---

### Post by cortman on 2013-04-22
Have you tried setting the resolution for each with xrandr?

```
xrandr
```

to get the ID for each monitor (i.e., HDMI1, VGA1, etc.). Set with

```
xrandr --output HDMI1 1920x1080
```

obviously substituting the correct monitor ID for "HDMI1" and your desired resolution for "1920x180".

---

### Post by eyeneedhelp on 2013-04-24
thanks, that,like everything is new to me,a newcomer to linux. so i will explore it next,im a minute from deep sleeep!!
i do enjoiy the challenge and i like the command line if i can get to understand it..tomorrow...

---

