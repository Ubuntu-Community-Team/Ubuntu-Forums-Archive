---
title: "2 problems I have"
date: 2007-08-23
forum: General Help
---

### Post by slayer04 on 2007-08-23
ok I have 2 problems which I couldn't find help for, first is I am using the totem player ubuntu had when I installed it and it played videos just fine but I upgraded my windows to service pack 2 and now all the videos I play in the Totem player the color is messed up it looks like it's inverted so I messed with the contrast bar and more didn't work returned everything to default, didn't work I don't understand it because before upgrading windows everything was fine? 2nd it when I click on desktop effects I get Composite extension is not available which I am guessing means I need to download something I just need to know where?


P.S. funny fact when I take a screenshot in the totem player it looks normal go figure!

---

### Post by will71110 on 2007-08-23
I have this problem but it's usually in windows XP.  I found that if you have WMV Acceleration on in an ATI driver setup, it does this.  Disabling it was the only way to rid of it.  Hope that doesnt mean I'm going to have that same issue in ubuntu.

---

### Post by imbjr on 2007-08-23
Take a look at this:
[https://answers.launchpad.net/ubuntu/+source/totem/+question/7373](https://answers.launchpad.net/ubuntu/+source/totem/+question/7373)

Specifically, the bit about:
ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink

That might be the solution.

---

### Post by slayer04 on 2007-08-24
this looks like it will help thanks I will try it... and let you know if it works

---

### Post by slayer04 on 2007-08-26
sweet that guide worked thanks but I still don't have desktop effects working

---

