---
title: "NVidia Screen Tearing"
date: 2014-02-08
forum: General Help
---

### Post by jarrettlolhi on 2014-02-08
Hello, I recently got an NVidia GTX 570. After installing the proprietary drivers via "Additional Drivers", I've noticed severe screen tearing and I can't seem to fix it.
It seems like I've tried everything, here's what I've done:

NVidia XServer Settings:
Enabling "sync to vblank"
Disabling flipping
Going into "maximum performance" mode

Compiz settings:
Disabling "detect refresh rate"
Disabling "unredirect fullscreen windows"
Manually setting the refresh rate to to the double of my monitor's refresh rate (120)
Disabling "composite"
Disabling "opengl"
Disabling all effects

I'm using two monitors, I read in some places that this can cause tearing as well. But the tearing still occurs after disabling either one.
I've also tried ALL of the driver options available to me. Here's a list:

NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-319(proprietary, tested)
NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-319-updates(proprietary)
NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-304(proprietary)
NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-304-updates(proprietary)
Nouveau display driver from xserver-xorg-video-nouveau(open source)

I've even re-installed Ubuntu.

The tearing is noticeable on the edges of windows when dragging them. It's also very noticeable when scrolling in web browsers, as well as in both video-games and videos (particularly in scenes which pan slowly)

I've tried everything I can find, and everything I can think of, what should I do?

---

### Post by sdowney717 on 2014-02-08
Does this help?
[http://www.youtube.com/watch?v=Sw7s5M3fgcE](http://www.youtube.com/watch?v=Sw7s5M3fgcE)

---

### Post by jarrettlolhi on 2014-02-08
Unfortunately not

---

