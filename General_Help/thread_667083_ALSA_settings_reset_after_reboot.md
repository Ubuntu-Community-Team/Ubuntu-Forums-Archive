---
title: "ALSA settings reset after reboot"
date: 2008-01-14
forum: General Help
---

### Post by malfist on 2008-01-14
For some reason I have to reconfigure alsamixer's settings everytime I boot up, can someone help me fix this?

---

### Post by malfist on 2008-01-14
It was working, then I installed a new sound card that didn't work. Then I reinstall the old sound card, and in the process I had to recompile/install alsa, and now it doesn't keep the settings.

---

### Post by matthewcraig on 2008-01-14
It is likely the default card is not being associated with your card.  Look into setting that with the /etc configuration file.

---

### Post by malfist on 2008-01-14
What config file? I know of only the one in the home folder (although I know there is another, I don't know what it's called). According the the sound settings in System->Pref->Sound C-MEDIA (ALSA driver) is set as the default sound device.

---

