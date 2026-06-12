---
title: "My dream MAME rig - how can I set this up?"
date: 2007-12-22
forum: General Help
---

### Post by CaptSaltyJack on 2007-12-22
I have an idea to set up a Linux box next to my LCD TV,  plug it via DVI->HDMI, and basically have a dedicated MAME box.  I'd like to have it set up so we can browse and choose games via a gamepad (no typing/keyboard).

Any suggestions would be appreciated!

---

### Post by bwhite82 on 2007-12-22
This is an interesting idea. Off of the top of my head I can't see it being too difficult, just need the right video card and perhaps a USB game pad, configured to act as a mouse. It wouldn't be too glamorous though, you'd basically see your UB desktop on your screen and simply use the game pad to navigate to MAME.

---

### Post by CaptSaltyJack on 2007-12-28
Anyone have any advice?  I've tried compiling and installing AdvanceMenu/AdvanceMAME.. without much luck.

---

### Post by Craigus on 2007-12-28
Have a look here:

[http://www.tech-geeks.org/geeklog/article.php?story=20060503193019113]("http://www.tech-geeks.org/geeklog/article.php?story=20060503193019113")

---

### Post by CaptSaltyJack on 2007-12-28
I got it working.  Only two things are puzzling me:

1) Joystick doesn't work.  In Ubuntu, it works fine.  I installed the joystick calibrator and it can see it just fine, but when I try to assign up/down/left/right to joystick movements in AdvMame, it doesn't detect it.

2) The device_video_output 'fullscreen' option is kinda wonky.  It goes larger than full screen a little, and the bottom of the screen is cut off.  Yet, if I start in windowed mode, then hit alt-enter to full screen it, it's perfect.

---

### Post by jpcline004 on 2008-02-08
Make sure you have enable the joystick in the default game settings. 

Also, make sure you manually set the fullscreen resolution. I think it is auto detecting and that is the problem. Check out my link for my rig (using PC).

[http://thelivingroomarcade.net/setup](http://thelivingroomarcade.net/setup)

---

