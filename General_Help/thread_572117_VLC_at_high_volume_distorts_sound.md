---
title: "VLC at high volume distorts sound"
date: 2007-10-10
forum: General Help
---

### Post by B-Con on 2007-10-10
When playing an audio file in VLC the higher I put the volume the worse the distortion is of the output, even if I lower my speaker and Master volume, so it isn't a volume issue.

For example, if I put the VLC volume at 50% and adjust my speaker volume so that it's at a comfortably soft volume it sounds distorted and staticy. If I slide the VLC volume down to something more like 5% and increase my speaker volume to compensate and hold the final output volume the same, the quality is basically perfect. But the higher the VLC volume goes the worse the quality gets.

This only applies to audio files (MP3 to be specific), video files with audio sound fine.

---

### Post by nzadLithium on 2007-10-10
yeah same here. I don't worry about it though. I set my default volume to about 25% then just use my speaker volume to control sound output. My speakers can go more than loud enough even when vlc is set to 25% so yeah.

---

### Post by B-Con on 2007-10-10
Yeah, it's not a critical issue. I can get the audio loud enough with my speaker volume too, it's just annoying. I'd prefer to be able to adjust the sound for VLC to match my speaker volume, that way my speaker volume is always constant and all applications are scaled to it. (And 25% for me is still bad quality, I really can't go above 15% without it getting too annoying.)

---

### Post by aparigraha on 2007-10-10
Having the same problem myself. One thing to check first to make it a little better is the PCM setting in alsamixer. Worked for me.

In a terminal window type: alsamixer. Navigate to PCM with arrowbuttons on keyboard. Make sure there is no PCM dB gain (up/down arrows). It should read 0.00, 0.00 under "Item" above. And the scale should be set to a maximum of 74%.

---

### Post by FuturePilot on 2007-10-10
Probably doesn't help much, but I've got the same problem. 
This might be related to the problem
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/103025]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/103025")

---

