---
title: "IBM Thinkpad T30 running Hardy &amp; CCSM"
date: 2008-06-24
forum: General Help
---

### Post by shellhrs on 2008-06-24
Just an info:

I did a clean install of Hardy over Feisty because I've been told that Hardy supports desktop effects better than Feisty (I had rotating cube on Feisty). But even though my system have no restricted drivers installed, it's unable to run any desktop effects.

Apparently, Hardy doesn't recognize Radeon Mobility 7500 in my system (unlike Feisty which recognized it automatically). So, I modified my xorg.conf according to [http://help.ubuntu.com/community/RadeonDriver]("http://help.ubuntu.com/community/RadeonDriver").

Still, desktop effects can't be enabled. So, I installed xserver-xgl from Synaptic, and voila, all desktop effects are available. :lolflag:

By the way, if I didn't modify the xorg.conf, and only installed xserver-xgl, I would get the desktop effects, but the movement would be very slow (I've tried this before :)).

---

### Post by Forlong on 2008-06-24
You didn't need to do any of that.
First thing you should do is getting rid of Xgl:
```
sudo apt-get remove xserver-xgl
```

Afterwards restart X and then use this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by shellhrs on 2008-06-26
Forlong, thanks for the input.

I tried your suggestion, and apparently ATI card is blacklisted, so I answered yes to the question to skip the blacklist check. And now I have the effects running smoothly and faster, even better than before (especially no more white lines left on the screen).

Thank you very much!

---

