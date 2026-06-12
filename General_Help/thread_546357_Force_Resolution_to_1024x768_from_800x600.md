---
title: "Force Resolution to 1024x768 from 800x600"
date: 2007-09-08
forum: General Help
---

### Post by climbjm on 2007-09-08
**The Setup:**
I have  a desktop running Ubuntu FF.

It has no mouse, keyboard or monitor hooked up to it.
It is powered on and hooked to the network.

I can SSH and VNC into it just fine.

**Desired Result:**
When I VNC into my box, it is at 800x600 and I want to know if anyone knows how to force that to 1024x768 so when I VNC into it, I can actually see the screen.

:confused:

---

### Post by chalex on 2007-09-08
Which VNC server are you using?  Isn't there a way to set the screen size in the VNC server configuration?  

Which VNC client are you using?  Isn't there a way to set the screen size in the VNC client configuration?

---

### Post by climbjm on 2007-09-09
I am using Ultra VNC as the client. (I really like it)
I am using the Default version of VNC that Ubuntu comes with for remote desktop.

However I dont think it has anything to do with the VNC settings.
Doesn't the computer set the resolution size when it boots/logs in?

If I try to use the "Change Screen Resolution" tool the max is 800x600.

---

### Post by fragos on 2007-09-09
If you've never installed a video diver in that remote box you'll probably be running vesa which will limit available resolutions.

---

### Post by theWrkncacnter on 2007-09-09
I've had to correct faulty auto-detections a few times. The way that works the best is just googling your monitor's horizontal and vertical refresh ranges. Then run sudo dpkg-reconfigure xserver-xorg, choose advanced monitor setup or whatever it's called, and plug in these values. Also make sure you're using the right driver for your card. You can choose the defaults for most questions.

---

