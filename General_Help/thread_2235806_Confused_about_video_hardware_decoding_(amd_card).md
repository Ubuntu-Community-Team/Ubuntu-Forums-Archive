---
title: "Confused about video hardware decoding (amd card)"
date: 2014-07-23
forum: General Help
---

### Post by ed123488 on 2014-07-23
Greeting all,

I have a general question about video hardware decoding with amd card (HD5450)
I use this card for years and my CPU is Ivy bridge i5-2500, kernel version 3.15 for now. 
Months ago, amd release UVD support for open source radeon driver.
Kernel version > 3.10 should support it, and VDPAU has also begun to be supported via a Gallium in mesa.

There are some confused point to me,below
1. What is mesa doing between driver and VDPAU?
2. When I playing a 1080p. mkv movie with mplayer(vo=xv not vdpau, actually I cannot use vdpau), my cpu usage is under 10% for each core, is that mean hardware decoding enabled? I was satisfied with it now, enable VDPAU support will take any benefit for now?  (mkv playback with kernel 3.7 an 3.15 makes no difference)
3. How to confirm that hdmi audio and dpm function are enabled with kernel 3.15 ? or these two functions have enabled by default? (I have attached kernel parameter radeon.audio=1 and radeon.dpm=1)

---

