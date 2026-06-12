---
title: "Audio problems after Hardy Upgrade."
date: 2008-04-27
forum: General Help
---

### Post by Crowchild on 2008-04-27
After I made the move to Hardy my sound levels are very low on all media types when the volume is maxed out.

It was working fine before. Any ideas?

---

### Post by marcusfurius on 2008-04-27
I also had some sound issues with Hardy. What you could try is changing your sound preferences devices to ALSA over the new PulseAudio Sound Server. I did this and it fixed my sound issues. You can do this as follows:
Select SYSTEM-PREFERENCES-SOUND
Now, on the Devices tab, change your devices from PulseAudio to ALSA (or an other one).

Good luck.

---

### Post by Crowchild on 2008-04-27
Okay, so changing it to pluseaudio seems to have improved the problem  with respect to the head-phone jack (though not solved it). Still the built in speakers are almost inaudible.

---

### Post by Dubbayoo on 2008-04-27
> **Crowchild said:**
> Okay, so changing it to pluseaudio seems to have improved the problem  with respect to the head-phone jack (though not solved it). Still the built in speakers are almost inaudible.

He said change it to ALSA, not PulseAudio.

---

### Post by Crowchild on 2008-04-27
With ALSA, the sound is still quiet.

---

