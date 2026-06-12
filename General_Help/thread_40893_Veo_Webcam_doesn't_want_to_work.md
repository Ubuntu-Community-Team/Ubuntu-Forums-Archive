---
title: "Veo Webcam doesn't want to work"
date: 2005-06-10
forum: General Help
---

### Post by Masato on 2005-06-10
I tried installing my Veo Stingray webcam and it doesn't want to work. I went into Camorama and it keeps telling me there is no device in /dev/video0. Can it work or is there a way I can get it to work?

---

### Post by tymek666 on 2005-07-30
I have the same problem with veo camera, but i've found some info that it's possible to use this webcam under linux with ibmcam driver.

[http://www.linux-usb.org/ibmcam/](http://www.linux-usb.org/ibmcam/)

---

### Post by heimo on 2005-07-30
At least some people are having bad luck:
[http://www.leenooks.com/205]("http://www.leenooks.com/205")

But it may be supported by ibmcam module (which is in kernel):
[http://www.linux-usb.org/ibmcam/]("http://www.linux-usb.org/ibmcam/")

---

### Post by tymek666 on 2005-07-31
Ok, i figured it out. Veo cam is supported in ubuntu :)
I've checked only GnomeMeeting before and it didn't work...but this camera seems to work with camsteam (you can install it with Synaptic).
To using camera with Gnomemeeting you have to install V4L (not V4L2 which comes with ubuntu) using also synaptic.
Best wishes,

---

### Post by macgyver2 on 2005-07-31
[QUOTE=tymek666]Ok, i figured it out. Veo cam is supported in ubuntu :)
I've checked only GnomeMeeting before and it didn't work...but this camera seems to work with camsteam (you can install it with Synaptic).
To using camera with Gnomemeeting you have to install V4L (not V4L2 which comes with ubuntu) using also synaptic.
Best wishes,[/QUOTE]

Just dug out my old Stingray...I found it also works with xawtv and v4l2.

[QUOTE=Masato]I tried installing my Veo Stingray webcam and it doesn't want to work. I went into Camorama and it keeps telling me there is no device in /dev/video0. Can it work or is there a way I can get it to work?[/QUOTE]

I do like camorama, though, so maybe I'll add the v4l "downgrade" and see if that fixes the camorama issue.

---

### Post by tymek666 on 2005-08-01
Yes, it also works with V4L2, but not in gnomemeeting....

---

