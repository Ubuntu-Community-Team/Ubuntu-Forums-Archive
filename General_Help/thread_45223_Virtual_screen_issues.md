---
title: "Virtual screen issues"
date: 2005-06-29
forum: General Help
---

### Post by Funzo on 2005-06-29
Hi all,

My X is configured to run at 1600x768 virtual and 1024x768 viewing. I added  Virtual 1600 768 to my xorg.conf.

I've noticed that fullscreen in Totem will stretch across the entire virtual screen. Which is unwatchable.

With Mplayer it scales the video correctly using the -zoom option but there is still the left and right black space. So I have to manully centre the video with the mouse.

When I was using Slackware, Mplayer/TVtime would do proper fullscreen, so that I didn't have to fiddle around with centering the video. I was running at 1600x1200 virtual then.

Does the X server in Ubuntu have direct access to the graphics card? I'm guessing it must have gone through some X layer which might explain why the video is being displayed at 1600x768 as oppose to the natural resolution.

Another thing I noticed is that my compiled mplayer is missing the "xv" option for -vo. But the X log file claim it has loaded XVideo. I never had to fiddle with this option so not sure what that is responsible for.

---

### Post by Funzo on 2005-06-29
Solved my problem this morning. 

Turns out I was missing some libxv-dev package, which Mplayer was looking for when I was compiling it from source. Plus other devel packages which weren't installed by default.

I notice Ubuntu tends to leave out a few development package in general.

---

