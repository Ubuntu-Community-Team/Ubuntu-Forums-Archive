---
title: "Sound Not Working after LightDM fix"
date: 2015-09-16
forum: General Help
---

### Post by chemist931 on 2015-09-16
So a few days ago, LightDM wouldnt start and stopped the boot process.  I purged and reinstalled LightDM, and it was fixed immediately, except now the speakers do not work.  I looked and found that the sound card is not recognized.  In sound settings, a box with audio devices is displayed, except none are there when they used to be.  I updated the drivers, ran alsamixer, and all the libs are there. The sound card can actually be found in the terminal, no error messages, but sound won't play through it.  How do I fix this?

---

### Post by Geoffrey_Arndt on 2015-09-17
If not already installed, might be worth a shot to install "pavucontrol" . . .

---

### Post by chemist931 on 2015-09-17
Didn't work, I don't use PulseAudio.

---

