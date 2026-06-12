---
title: "C-Media USB Headphone Set wont work properly"
date: 2007-07-04
forum: General Help
---

### Post by mattyrigby00 on 2007-07-04
well i fixed that i couldnt get sound in java/flash by deleting the amd64bit version and putting 32bit on and using standard firefox - now i have another problem, my headset wont work in ubuntu, i cant figure out any way to switch between my soundcard and the usb headset. is there a way to do it or would i just need to get a new soundcard (my current one's microphone jack is broken) and a new headset (i dont feel like buying a new headset and soundcard just for linux though :() i can get the "test" working but nothing else goes to it.

---

### Post by luctor on 2007-07-06
What excactly are you trying to do.
Use the headset for certain programs only ?

---

### Post by KalTorak on 2007-12-07
solved: [http://forum.ubuntu-it.org/index.php?topic=37337.msg195132#msg195132]("http://forum.ubuntu-it.org/index.php?topic=37337.msg195132#msg195132")

just one thing: c-media headphones is 'blacklisted' in alsa-base
just put a # under # #Prevent abnormal drivers from grabbing index 0 where it gives a -2 to your usb sound card (the headset)

---

### Post by brujoand on 2008-02-13
Glad you got it working. I have the same soundcard, and it worked outofthe box in 7.10 BUT the volumcontrol is pretty messed up. Its impossible to manage in the gnome-volum-manager because the volum jumps up and down like crazy. I can sortof manage it in alsamixer but still the sound is a little of balance and hard to adjust low. Any clues here?

---

