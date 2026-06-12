---
title: "starting video streams causing audio to cut out"
date: 2016-09-19
forum: General Help
---

### Post by thedaemon69 on 2016-09-19
So, made an intel nuc based home theater pc to replace an older system. Using ubuntu 16.04. by and large does it job excellently....


Every so often, however, there's a strange bug in the audio output. I'll be watching some videos on youtube or whatever, and I'll open something new and the audio cuts out, for anywhere up to about 10 minutes. It never cuts out in the middle of a stream or anything, only when opening a new one. It happens most often when opening a stream in a new window. So far, it seems to happen with any random streaming video source. I've done a lot of hunting around for potential solutions and more information about what, exactly, is going on, but nothing quite matches what I'm experiencing. 

The bug is definitely triggered in firefox, and can I do it fairly reliably (not 100%, but if i open a video in a new window there's a decent chance it'll happen)
I'm pretty sure I've seen it happen in chromium too, but if so, it's harder to trigger
When the bug kills the audio, it does so across the board - it's not just that particular stream being silent, /everything/ goes quiet - other windows, vlc... nothing can make any noise, including the audio test buttons.
It just comes back anywhere from a few seconds to over 10 minutes later. 
Pulse Audio volume control is still showing active audio from whatever programs are currently trying to make noise - it's receiving all the appropriate audio data, it's just that it doesn't make it to the HDMI output for some reason.

I know the TV and HDMI cable are fine, and problems with either of them wouldn't manifest in audio cutting out only when starting new video streams.

Intel NUC 6I3SYH / 8gb ram / integrated graphics card / ubuntu 16.04

---

### Post by HeWhoIsCalledB on 2016-10-10
I have the exact same problem on Ubuntu 16.04.1 x86_64.  Seems to bee triggered by watching YouTube videos in Google Chrome.  Restarting my machine fixes the problem, until it happens again.  I haven't found any other fixes.  Ubuntu runs flawlessly otherwise.

My system:
Toshiba Satellite L755-S5362
Sandy Bridge Intel Core i3
2 x 4 GB DDR3-1333
Intel HD Graphics 3000

---

### Post by thedaemon69 on 2016-11-07
I've mostly had it in Firefox myself. Doesn't matter whether HTML or flash video either from my later testing. Still haven't found a solution other than rebooting or waiting the completely random length of time for it to magically start working properly again either. :(
Rebooting with an SSD is quick, but this is silly.

---

