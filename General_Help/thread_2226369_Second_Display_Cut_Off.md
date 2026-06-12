---
title: "Second Display Cut Off"
date: 2014-05-26
forum: General Help
---

### Post by mortrca on 2014-05-26
I am having a problem with my dual monitor setup in Ubuntu 12.04 that is causing the second display to be cut off along the left edge (the edge where the two displays meet). If I move my mouse between the displays, it is not visible while moving over the distance that is being cut off (approximately 200 pixels). If I use the monitor settings to move the image horizontally, some of the "cut off" image becomes visible, but my monitor does not allow for a large enough correction. I had this setup working for quite a while, but after a recent reboot I started experiencing this. I have tried adjusting some settings in nvidia-settings, but I don't know what I'm doing and nothing I tried worked. Suggestions?

---

### Post by zemega on 2014-05-26
I would suggest boot with only one monitor first. Then plug in the second monitor. See if that helps. Or you can go into displays and move around the screen positions. Maybe that will help you.

---

### Post by mortrca on 2014-05-27
The primary monitor works fine, the image is properly displayed and if I remove the second monitor, using just the first monitor works as it should. Unfortunately, I haven't been able to get from that point to having both monitors work again.

---

### Post by mortrca on 2014-06-30
I still have not been able to fix this. I thought I'd try a clean slate, so I erased 12.04 and installed 14.04, but I am experiencing the same issue. Both monitors are 1920x1080 and approximately 1.5 inches on one side of the second display is black. A corresponding 1.5 inches of the screen is "hidden" in between the two screen (making it not visible). The one thing that did (sort of) fix this issue was telling Ubuntu to make the second display a lower resolution, but that isn't a viable permanent fix.

---

### Post by HermanAB on 2014-07-01
You should be able to fix it with a little script for xrandr.

---

### Post by mortrca on 2014-07-12
Unfortunately, I have fixed this issue without knowing how. I started looking into xrandr, but didn't get very far before the screen flashed and everything looked right. Thanks for your suggestions.

---

