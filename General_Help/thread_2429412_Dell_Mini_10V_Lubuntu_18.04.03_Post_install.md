---
title: "Dell Mini 10V Lubuntu 18.04.03 Post install"
date: 2019-10-17
forum: General Help
---

### Post by irving-liaw on 2019-10-17
I've recently installed Lubuntu on a previously Hackintoshed Dell Mini 10V.

Two problems post installs have been:
[LIST=1]
[*]Generally sluggish performance and display
[*]Youtube on Chromium is choppy at best.
[*]Webcam doesn't work (tried cheese already)
[/LIST]

Anyone can provide any insight?

---

### Post by mikewhatever on 2019-10-18
The sluggishness part is expected. The modest Dell Mini 10's hardware was weak 10 years ago, and hasn't been getting any newer or faster since, so that both the CPU and graphics are completely inadequate in 2019. 
The webcam problem needs troubleshooting, for which you haven't provided any info to work with.

---

### Post by mörgæs on 2019-10-18
If you have empty slots for memory then adding some more will change a lot.

The output from ```
sudo lshw -C memory
``` will show the status.

---

### Post by TheFu on 2019-10-18
> **irving-liaw said:**
> I've recently installed Lubuntu on a previously Hackintoshed Dell Mini 10V.

Two problems post installs have been:
[LIST=1]
[*]Generally sluggish performance and display
[*]Youtube on Chromium is choppy at best.
[*]Webcam doesn't work (tried cheese already)
[/LIST]

Anyone can provide any insight?

The Atom N270 CPU is the issue with only 270 passmarks.  The "270" result is just a coincidence. I had an Asus Eee with that CPU in 2010.  It was fine for minimal work loads that didn't need any GPU.  These days, any server-like workloads for a CPU like this, I'd put on a Raspberry Pi v3/v4.

Back then, the onboard GPUs didn't support mpeg2 or h.264 video decoding, so that all has to be done using the CPU, which is anemic. I did extensive video testing back then for my job and found 600p and less resolutions would work fine.  Any higher resolution videos skipped or wouldn't play at all. I re-purposed the machine as an XBMC system until hidef content became common, then I gave it away and spent $100 for a faster, replacement, machine.  At this point, a 2013 Acer C720 Chromebook would be about 5x faster and supports smooth video playback thanks to newer iGPU with on-chip video codec support.  Just be certain to get a Celeron 2995U CPU (1500+ passmarks). Should be able to find these for about $65 on ebay. This assumes that cheap is more important than good.  Chromebooks are made with extremely cheap keyboards. I've worn out 2 just from typing. Besides the broken keys, I have 2 that 

As for the webcam, I've never seen *cheese* work, but I have had luck with many other tools.  One of them begins with UVC.... something. I'm on a different system and don't have any webcam-specific software loaded.  OBS worked ok on that C720 chromebook running Ubuntu, but OBS is relatively more heavy/capable than what the N270 can handle.

Heck, if you seek a video playback device that isn't a laptop, get a Raspberry Pi and load up Kodi.

---

### Post by uRock on 2019-10-18
Can you view the webcam using vlc? To do this, open VLC, click Media in upper left, then click Open Capture Device, then click on the video device name dropdown and select the first option, then click Play.

Also, please post the output of ```
lsusb
```and```
lspci
```

---

