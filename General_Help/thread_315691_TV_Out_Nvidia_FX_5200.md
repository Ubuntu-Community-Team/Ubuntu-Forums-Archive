---
title: "TV Out Nvidia FX 5200"
date: 2006-12-09
forum: General Help
---

### Post by loyd86 on 2006-12-09
I have been playing with this for a while, but have been unable to get it to work. I have a TV hooked up by an svideo cabel to my GeForce FX5200 graphics card and I cannot get it to display anything. I would like for it to clone the out that is going through the RGB to my monitor. 

I have tried following [http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456) howto with no success. 

I have tried to install nvtv, and it recognises my video card as "GeForce FX 5200 (01:00.00)", which is correct, but for the TV Encoder it comes up with about 8 chips that are all labeled "Unknown chip (0:A0)" and "Unknown chip (0:A2)" all the way to AE. Any ideas of what to do woud be great.

---

### Post by PriceChild on 2006-12-09
If you have installed the nvidia proprietory codecs, then you should be able to:
```
gksudo nvidia-settings
```If you've got a 9*** driver then you can edit these settings in there. You might also be able to with 8*** but I'm not sure.

if not, then get back to me.

---

### Post by loyd86 on 2006-12-09
NVIDIA Driver Version 1.0-8776

Under display device I see only my monitor and do not see anywhere to enable the TV-Out.

Should I try to get the 9*** driver?

---

### Post by PriceChild on 2006-12-09
Strictly speaking, you can edit your xorg.conf manually to make these changes.

Personally though I'd go with [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy) or [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) method 2.

Then use the thing i described earlier.

---

### Post by loyd86 on 2006-12-09
After I got the driver installed it has not been working. Sometimes it detcets that I have a TV hooked up others it asks if I want to remove the TV because it has been disconnected. Could this have anything to do with the fact that my SVIDEO has an Svid to composite apadter hooked up to it in order to hook it up to my TV

---

### Post by loyd86 on 2006-12-09
Yeah. I am taking a look at the xorg.conf I belive that all the settings dialog does it write that for me. It looks like it is setup all correct but I still am not getting any picture on my TV.

---

### Post by loyd86 on 2006-12-09
If I hookup the svideo to my tuner card and rastart gdm then it will detect the tv out fine. I set the resolution to 640x480. I unhook it from my tuner and plug it into the composite and i get little bit of color and static on the screen, but nothing recognizable.

---

### Post by loyd86 on 2006-12-10
After I got the flickering I figured out that I could get video just fine when I changed out the cable I was using. I guess that was the problem. Thanks so much for the help.

---

