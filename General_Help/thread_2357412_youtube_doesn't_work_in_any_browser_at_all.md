---
title: "youtube doesn't work in any browser at all"
date: 2017-04-01
forum: General Help
---

### Post by opus1 on 2017-04-01
Running xubuntu 16.04 on a System76 meerkat.  Youtube doesn't play whatsoever in *any* browser.  I have tried vivaldi, firefox (safe mode), pale moon and the results are all the same: the video appears stuck on loading (the spinner in the player spins), but it never starts. I can run the progress bar across the bottom and see the little preview thumbnails. Where ever I stop the progress bar I get a still image of the video, but pushing "play" does nothing.

The first time this happened, I can't remember if I just waited or rebooted, but it started working again.  Now, it has been this way for days, and after a couple of reboots.

I have a laptop running xubuntu 16.04 and youtube plays just fine. How on earth can I possibly troubleshoot this?

---

### Post by opus1 on 2017-04-01
It turns out that the problem was caused by my sound not working correctly (documented here: [https://ubuntuforums.org/showthread.php?t=2357393](https://ubuntuforums.org/showthread.php?t=2357393)).

I did a ```
sudo alsa force-reload
``` and my sound card appeared in the sound settings, the sound started working and youtube started working again.

---

