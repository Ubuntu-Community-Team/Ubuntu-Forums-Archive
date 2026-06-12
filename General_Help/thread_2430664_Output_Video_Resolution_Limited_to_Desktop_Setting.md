---
title: "Output Video Resolution Limited to Desktop Settings"
date: 2019-11-05
forum: General Help
---

### Post by N_mag on 2019-11-05
Setup: I have a pretty fresh install of Ubuntu 19.10 /w proprietary Nvidia drivers on Xorg playing on a Samsung NU8000 4k TV

Issue: When I am playing Dark Souls 1 from steam using Proton, the video resolution will not go above what the desktop resolution is set at.

Description and Reasoning: My TV is capable of doing 1440p at 120Hz and 4k60, however, the PC will not detect that special 1440p120 without the desktop being set to it. However, not all games do I want to play at that setting, for instance, Dark Souls looks good enough and fluid enough that I would rather just stick it on 4k60 and let it ride, but other games like Doom 2016 I want it on 1440p120 because 120 is pretty dang smooth ofc, but like I said, if I don't have the TV set on 4k60 then the games think that it can't go above 1440p AND if the desktop is set on 4k60 the games think that the 120Hz option for 1440p is not available but only the 60HZ.

I've tested that 1440p120 does work when the desktop is on it and the game can use it just fine, but since Nvidia doesn't support freesync over HDMI I don't use it since there is occasional drops in FPS and there's tearing since vsync is unavailable with 120Hz modes.

Hopefully that was clear enough. Basically the desktop is limiting the games' choices they have and when the desktop isn't set on 120Hz games think it's not available at all.

Also, I've tried looking at the [xorg wiki]("https://wiki.ubuntu.com/X/Config/Resolution") for setting resolutions but I don't know if all that fidling is worth it, plus it's pretty confusing to me :(

---

