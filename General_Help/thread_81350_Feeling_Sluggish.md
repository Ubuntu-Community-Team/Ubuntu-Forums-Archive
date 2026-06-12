---
title: "Feeling Sluggish"
date: 2005-10-24
forum: General Help
---

### Post by sailor420 on 2005-10-24
I'm running Ubuntu Breezy on my laptop, and I love it, except for one thing: it just "feels" sluggish. I'm not sure I could measure it, but window movements, program openings, browser pageloads... It all just feels a bit slow. I dont think its my computer, its got a gig of RAM and an Intel Mobile 1.5GHz processor. I don't have any eye candy turned on either, at least nothing beyond whatever Ubuntu enables by default.

Any suggestions on how to maybe speed it up? I was thinking maybe the video drivers, but as my video card (ATI Radeon 7500 Mobility) isnt supported by the Radeon drivers, I don't think I have a choice.

Many thanks...

---

### Post by erzhong on 2005-10-26
See whether this link helps.

[http://ubuntuforums.org/showthread.php?t=29990&highlight=radeon+mobility+7500+driconf](http://ubuntuforums.org/showthread.php?t=29990&highlight=radeon+mobility+7500+driconf)

My laptop is a IBM T42, with Radeon Mobility 7500, and 1400x1050 LCD.  Radeon works fine in 2D, but DRI driver has bugs in 3D.  

You need to install both common package and radeon package from the DRI website.  The confusing thing is that both packages are extracted to a folder, and of the same name, though the contents are different.  You can put the two packages into two directories to avoid the confusion.

---

