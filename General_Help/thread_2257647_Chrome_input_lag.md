---
title: "Chrome input lag"
date: 2014-12-21
forum: General Help
---

### Post by SantinoC on 2014-12-21
I am running 14.04 on a Lenovo Yoga 2 pro.

I have chrome Version 39.0.2171.95 (64-bit)

I'm experiencing some weird behaviour in Chrome since upgrading to the latest Intel Graphics drivers.

Here is a youtube video i made that shows the issue. [https://www.youtube.com/watch?v=_WQjYtdiCSE](https://www.youtube.com/watch?v=_WQjYtdiCSE). You'll notice that sometimes the selection within the context menu skips every second option. This same behaviour is present within drop down lists as well.

The other issues I'm experiencing not shown in the video is lag when typing in textfields and selecting text.

I've tried disabling pepperflash in Chrome://plugins to no avail.

I tried reverting the graphics drivers, but for some reason it actually removed the Ubuntu-desktop package and really messed things up until I re-installed the video drivers and re-installed Ubuntu-desktop.

Here is some information from "glxinfo"
> name of display: :0

display: :0 screen: 0

direct rendering: Yes

server glx vendor string: SGI

server glx version string: 1.4

client glx vendor string: Mesa Project and SGI

OpenGL vendor string: LunarG, Inc.

OpenGL renderer string: Gallium 0.4 on Intel(R) Haswell Mobile

OpenGL version string: 2.1 Mesa 10.5.0-devel (git-d11c1c1 2014-12-18 trusty-oibaf-ppa+gallium-nine) OpenGL shading language version string: 1.30

I did try this, [http://askubuntu.com/questions/301930/downgrade-a-bunch-of-packages/405453#405453](http://askubuntu.com/questions/301930/downgrade-a-bunch-of-packages/405453#405453), but I'm still experiencing the same issues.

Sorry for the long winded question.

Any help would be greatly appreciated.

Thanks.

---

### Post by kerry_s on 2014-12-23
i had that issue to, had to dump google chrome for the open source version chromium web browser, after that it was all good.

---

### Post by SantinoC on 2014-12-24
I'm having the same issues in Chromium as well. 

I tried switching to firefox but since i use Google Hangouts, i need chrome installed. Even leaving chrome installed and JUST using hangouts is a pain because any link i click on from a hangouts chat window automatically loads chrome. 

I haven't been able to find ANYTHING online regarding this. It's very frustrating.

---

### Post by kerry_s on 2014-12-24
seems to come & go for me, so i went back to chrome, plus netflix only works in chrome. i did grab epiphany-browser just for bouncing around the web, very fast.
i only use hangouts on my ipod, so haven't come across that issue, sorry.

---

### Post by kerry_s on 2015-01-09
it's composting, try the fallback session, with the 2d version. just log out, click on the little gear thing if i remember right (sorry, i moved on to a different os) it should have some option to run on lower graphics.

---

