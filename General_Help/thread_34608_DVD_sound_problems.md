---
title: "DVD sound problems"
date: 2005-05-15
forum: General Help
---

### Post by mcelroyj on 2005-05-15
I'm running Hoary on an Intel 3.2GHz P4 with a SoundBlaster Audigy 2 and an nVidia 5700 graphics card.

Whenever I play a DVD I get strange clicks and pops randomly throughout playback.  I am using the ALSA drivers in VLC, however the problem also occurs when I use eSound.

From looking at the verbose output of VLC, it looks like VLC is using a52 -> fl32 as an audio filter to an fl32 mixer running at 48000 Hz stereo.

I've followed the instructions posted elsewhere on this site for getting ALSA sound working under ubuntu.

Thanks for any help or idea.

Jeremiah

---

### Post by agds on 2005-05-16
Here's a thought.  Have you tried with various different DVDs?

---

### Post by mcelroyj on 2005-05-19
Yes, this happens with every DVD that I own.

---

### Post by agds on 2005-05-19
Interesting.  What about playing other media, like CDs, directly from the drive?

---

### Post by mcelroyj on 2005-05-19
Pretty much any type of disk put in the drive makes the odd clicks & pops.

I managed to stop the problem by opening up alsa-mixer and turning off the first emu10k1 channel.  For some reason, that stopped the problem completely

---

### Post by djcraft on 2007-08-25
I have a Soundblaster Audigy 2 with the same problem. The pops and clicks typically come from the rear speakers for me this occurs even when I'm not playing anything with audio. I thought this might be due to a grounding issue, but the clicks only come from the rear speakers. Any thoughts?

---

