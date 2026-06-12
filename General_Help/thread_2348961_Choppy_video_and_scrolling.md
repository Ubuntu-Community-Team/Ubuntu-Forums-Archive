---
title: "Choppy video and scrolling"
date: 2017-01-09
forum: General Help
---

### Post by oldtimer2 on 2017-01-09
Running PC dual core 4 gigs did a fresh install with 14.04 and browser video and page scrolling is aggravatingly choppy. Auzus mother board with built in vid card. Any suggestions? New here.

---

### Post by TheFu on 2017-01-09
Welcome to the forums.

Need exact specs. "Dual core" could be VERY fast or dog slow.  You want to get HW accel with any videos during playback.  That means the videos need to be mpeg2 or h.264 encoded and one of the main 3 video card types - intel, nvidia or amd.  Other types of video cards are hit and miss on driver support.  Get the correct video driver installed first.

Inside a browser is a harder question. Not all browsers support hw-accel video. Not all video can be accelerated, so the CPU (which may be dog slow) will have to do all the work.  VP8, VP9, h.265 aren't often supported for HW accel video in a browser.  Just sayin'.

Anway, hope this provides some ideas for searching.

---

### Post by HermanAB on 2017-01-10
Bad choppy video and a 100% CPU load usually means that ffmpeg is running in emulation mode, due to a bad video driver.

---

### Post by oldtimer2 on 2017-01-10
Thanks I will install the correct driver for nvidia

---

### Post by TheFu on 2017-01-10
> **oldtimer2 said:**
> Thanks I will install the correct driver for nvidia

With Linux drivers, it is best to stay within the distro's package manager.  There should be a tab in the package manager GUI for "Other" drivers. Look for proprietary.  Once you install this way, the normal, weekly updates you do will keep them updated.  Because these drivers are proprietary, Canonical cannot  just install them automatically - or chooses NOT to do that. I suppose it is to avoid legal issues and the wrath of people like me who wish to avoid proprietary software whenever possible.  Not that I have much "wrath." ;)

The last choice is to get the drivers from the vendor.  That can causes issues and should only be done when the other methods either fail or don't fix whatever the issue is.

---

