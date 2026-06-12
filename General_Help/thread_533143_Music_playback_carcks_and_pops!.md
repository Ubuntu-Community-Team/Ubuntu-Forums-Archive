---
title: "Music playback carcks and pops!"
date: 2007-08-23
forum: General Help
---

### Post by fjf on 2007-08-23
I have an external usb sound card working fine as default sound device.  But the music playback is noisy, full of cracks and pops.  I've searched all I could, and I have enabled the realtime-lsm with a gid=29.  I Installed also the jack audio connection kit, but it does not solve the problem.  The messages I get from it are:

21:33:30.150 XRUN callback (91).
delay of 18389.000 usecs exceeds estimated spare time of 11600.000; restart ...
21:33:31.022 XRUN callback (1 skipped).
**** alsa_pcm: xrun of at least 0.007 msecs
21:33:35.394 XRUN callback (93).
delay of 19389.000 usecs exceeds estimated spare time of 11600.000; restart ...
21:33:37.142 XRUN callback (1 skipped).
**** alsa_pcm: xrun of at least 0.058 msecs
21:33:40.639 XRUN callback (95).

...and so forth.    Is there a way to increase the priority of the usb port?.  Increasing the priority of rythmbox to -20 does not help.  Any hints?.

---

### Post by fjf on 2007-08-23
bump

---

### Post by fjf on 2007-08-29
OK, I solved it, increasing the sound buffer size:

[https://answers.launchpad.net/rhythmbox/+question/6927](https://answers.launchpad.net/rhythmbox/+question/6927)

---

