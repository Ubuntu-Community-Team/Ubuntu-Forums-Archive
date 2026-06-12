---
title: "7 yr old laptop smoother mp4 playback than 4690k w16gb ram!"
date: 2016-07-24
forum: General Help
---

### Post by harrellsm on 2016-07-24
I just installed 16.04.1 LTS on USB HD.  If I use it on my high end 4690k with gtx960 gpu my ripped .mp4 videos skip during playback using VLC.  I boot my old laptop with same HD and playback is smooth.  I installed and configured using the 4690k desktop and have only used the neuveau driver.  The laptop is an old core 2 duo with nvidea m130 discrete. This isn't logical. If anything it should be the laptop that skips during playback. If you know what the problem might be it would be much appreciated.

Sean

---

### Post by mc4man on 2016-07-24
The issue is likely vlc, by default it automatically sets hardware-decoding and video output & often picks wrong. Try opening vlc > Tools > Preferences > Input/Codecs & disable Hardware-accelerated.. Under the video tab pick an appropriate Output, OpenGl GLX is ok.

---

### Post by mastablasta on 2016-07-25
> **harrellsm said:**
>   I installed and configured using the 4690k desktop and have only used the neuveau driver. 


it's written a bit strange but if all you have used on new GPU 960gtx is the nouveau driver then it makes sense itmight work worse than onthe old chip. the opensource drivers are reverse engineered using outputs from the chip and whatnot. so the newer hardware has worse support than the old one. in case you are using nouveau on both PC then try using proprietary driver on the newer card.

---

