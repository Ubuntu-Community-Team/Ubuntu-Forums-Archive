---
title: "Bluetooth headset/speaker in 13.10"
date: 2014-01-08
forum: General Help
---

### Post by cptrohn on 2014-01-08
OK, I know this has probably been asked 1000 times, and did some searches this weekend on the subject.

But I am getting no sound out of my bluetooth speaker or headset at all. And I am not a bluetooth wizard.   I have a DellXPS13u, my other devices are working great out of the box, (logitech bluetooth keyboard and mouse)

I can successfully pair both the speaker and the headset, both show up as connected.  I open up the sound settings and select the speaker/headset  from the menu, test the sound and it is still coming from the laptop speakers.  I close the sound settings, then open them back up and the system has reverted back to the internal speakers as default.  Is there something super simple that I am overlooking here? (wouldn't be the first time lol)

---

### Post by cptrohn on 2014-01-09
Nobody?

---

### Post by cptrohn on 2014-01-09
OK, I finally found the answer to this issue.  I installed pavucontrol for some more extended sound control settings for my sound devices.  Fixed the problem right away as soon as I installed it.   Why the heck isn't this installed in the OS by default?

Woring flawlessly now and I am a happy man jamming away right now.

---

### Post by elleP on 2014-08-09
I had the same problem, however I needed to actually use pavucontrol, in the Configuration tab, the profile for my bluetooth headset is set to "off", this needs to be set to "High Fidelity Playback (A2DP)" for me to be able to use it properly.

---

