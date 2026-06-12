---
title: "Sound in third party apps"
date: 2007-08-09
forum: General Help
---

### Post by dave.007 on 2007-08-09
Hi,
I have just got ubuntu after finally getting sick of windows, I have only used linux as a server before so I have no idea about sound setup.
The problem is that all the apps that come with ubuntu and can be added without adding extra repositories work fine with each other for example rythm music player and xmms but when I try to run another program at the same time which I installed myself such as teamspeak that program is the only one which will output sound and when I try to use xmms then it says the sound card is being blocked. I have tried recompiling the alsa drivers and its still the same.

Thanks
Dave

---

### Post by dave.007 on 2007-08-13
bump****

---

### Post by fluteflute on 2007-08-14
I have this problem too.

---

### Post by Steveway on 2007-08-14
That's not a bug that is a feature.
To prevent this you need to change all apps to use a soundserver like esd or pulseaudio, it will mix it all together and send it to Alsa.

---

