---
title: "TV as default monitor"
date: 2008-03-12
forum: General Help
---

### Post by renzokuken on 2008-03-12
Hi,

Is it possible to use a TV connected to an nvidia via S_VIDEO as the default and only monitor?

I have a spare PC lying around that i want to make into a media centre that goes behind my TV (not HD or flatscreen) just plain old CRT with scart/s-video .... i have the cable already) so i can watch/listen to media across the network on my TV etc.

Thanks

---

### Post by jakev383 on 2008-03-12
Yes, you can.  I use the Mythbuntu respin on a couple front end machines that are only hooked to TV sets that connect to my backend mythtv system.  If you just want to install Ubuntu and have it displayed on the TV, only advice I'll give is to either have the TV (and ONLY the TV) hooked up when you install it, or run ```
sudo dpkg-reconfigure xserver-xorg
``` when you're done to get the overscan set correctly or you'll lose the outside edges of your screen.

---

### Post by renzokuken on 2008-03-16
Thanks for the reply jake.

Ok, so I hooked up the PC to the TV (only) and booted the Gutsy Desktop CD. The splash menu appeared (albeit in black and white) and proceeded to load when selected start/install. However, when it got to the point where GDM is supposed to start it went completely blank.

How did you install it with only a TV connected? With the alternate cd? I suppose i could have hit Ctrl+Alt+F1 and reconfigured xserver that way (this has only just occurred to me)

Any ideas or advice though?

---

### Post by Darkdelusions on 2008-03-16
I had this issue when I was playing around with myth tv this might help you out a bit. Depending on how you installed the nvida drivers you might beable to go into the nvida control panel and change this option

[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)
[http://ubuntuforums.org/showthread.php?t=23628]("http://ubuntuforums.org/showthread.php?t=23628") <= This might be a little ezer to follow

---

