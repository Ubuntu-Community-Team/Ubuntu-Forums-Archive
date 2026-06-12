---
title: "Sound not working"
date: 2005-11-01
forum: General Help
---

### Post by Whatthehello on 2005-11-01
I have breezy 5.10. and i cant get sound working. i have tried everything in this topic mostly.

[http://ubuntuforums.org/showthread.php?t=84746&highlight=sound](http://ubuntuforums.org/showthread.php?t=84746&highlight=sound)

its still not working. i can hear like the GUI sounds and the boot up sound, but when i play videos or mp3's, sound doesnt come out. DO i need to install a driver or something?

---

### Post by RAOF on 2005-11-01
That thread seems somewhat specific to his setup.  Since you hear system sounds, your soundcard is obviously set up fine.  I would suggest changing the default audio sink for gstreamer to alsa.  You can find that setting under "System -> Preferences -> Multimedia Systems Selector".  Then try playing a movie in Totem.

If the sound doesn't work in xmms, it's generally the fault of xmms - try selecting a different output plugin (alsa, esd, oss, whatever) and seeing if one of them works.

---

### Post by Whatthehello on 2005-11-01
it doesnt work. and when i click done, it freezes

---

