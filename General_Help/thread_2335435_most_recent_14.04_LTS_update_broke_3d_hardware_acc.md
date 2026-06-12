---
title: "most recent 14.04 LTS update broke 3d hardware acceleration"
date: 2016-08-28
forum: General Help
---

### Post by ro44444444 on 2016-08-28
In order to be acceptably functional, my video card must use the fglrx AMD drivers (formerly Catalyst.) These have been deprecated on 16.04, so consequently I am limited to 14.04.

I recently ran my regularly-scheduled system update. It reverted my system back from the proprietary fglrx video driver to the open xserver-xorg-video-ati driver, which does not support hardware acceleration (and results in about 5 fps watching streaming video.)

The fglrx drivers are still found, and appear like they should be applicable. System > Software & Updates > Additional Drivers finds both fglrx and fglrx-updates, you can select them with the radio button and hit "apply changes." However it will just churn for a bit, then autoselect back to the open drivers without a warning dialog or notification.

How can I either force the fglrx drivers or roll back the most recent system update?

---

### Post by Bucky Ball on 2016-08-29
Welcome. Yes, you're between a rock and a hard place, but not forever. Eventually, things will be better than they were! AMD is on to it and a new driver for 16.04 is on its way. AMD is getting rid of fglrx and bringing in a new driver.

I can't help more than that but can [point you to some info]("https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/") you might find useful. For now, might be better to stick with 14.04 (supported until 2019) and keep your eyes and ears open for the new 16.04 driver and flip to that when it arrives. Good luck.

---

### Post by ventrical on 2016-08-29
You will find this thread interesting..

[https://ubuntuforums.org/showthread.php?t=2334989](https://ubuntuforums.org/showthread.php?t=2334989)

---

