---
title: "Sound worked... Then didn't."
date: 2006-11-06
forum: General Help
---

### Post by JesterofDoom13 on 2006-11-06
When I first updated from 6.6 to 6.10 sound was good. It was working fine in all my apps and such. Then I restarted my computer, and the only thing that has sound now is Rhythmbox Music Player. Other media players can't play, Ubuntu startup sound doesn't come up, and GAIM seems to have failed me also.

 I searched google endlessly(well until now) and found nothing that helped me. So I decided to reinstall Ubuntu and see if that'd help. Well.. It did help.. Until I restarted my computer again. Now I'm back and square one. 

 I've tried the [comprehensive sound problem solution guide]("http://ubuntuforums.org/showthread.php?t=205449"). I'll admit my computer can't get passed general step 4 even if I try the suggested steps in the *failure* part. 

 I'll also note that when I goto System > Preferences > Sound and use the test buttons I can hear just fine. 

 If it'll help, my sound card is the CM8748-CH6 with the ALSA driver cmipci. 

 Anyone think they know the answer?

---

### Post by teaker1s on 2006-11-06
from my experience you want to make sure that your applications are using same output as your system preferences eg. OSS MIXER secondly if you double click sound icon on the taskbar(gnome) you will see an advanced option with switches, you may need to enable these to get sound other than test sounds eg my trust branded cmedia card needs these to enable optical out.

---

### Post by JesterofDoom13 on 2006-11-06
> **teaker1s said:**
> from my experience you want to make sure that your applications are using same output as your system preferences eg. OSS MIXER secondly if you double click sound icon on the taskbar(gnome) you will see an advanced option with switches, you may need to enable these to get sound other than test sounds eg my trust branded cmedia card needs these to enable optical out.

 Yeah, I've checked the alsamixer so much with no luck.

 But with the other thing you said, how would I check to see what apps use what output? 

 I think a main point is is that it works until I reboot it. I don't touch anything and everything works before I restart.

---

### Post by JesterofDoom13 on 2006-11-07
Alright I fixed this. 

 The way I fixed it was by turning off the motherboard sound in the bios. Works great now. I'm once again in love with Ubuntu.

---

### Post by dannyboy79 on 2006-11-07
> **JesterofDoom13 said:**
> Alright I fixed this. 

 The way I fixed it was by turning off the motherboard sound in the bios. Works great now. I'm once again in love with Ubuntu.


oh, so you have a pci sound card? i don't think we knew that or at least I didn't. glad you got it solved.

---

