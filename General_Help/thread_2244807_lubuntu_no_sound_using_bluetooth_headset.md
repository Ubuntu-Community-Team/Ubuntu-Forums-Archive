---
title: "lubuntu no sound using bluetooth headset"
date: 2014-09-18
forum: General Help
---

### Post by porky.chops on 2014-09-18
Oh, kay..
i know this could be put in many places so i chose general as its not just specific, may it be hardware, software etc etc well here is some history..

running a poweredge server with no soundcard
installed ubuntu, put my bluetooth in and audio worked very well...
i installed the downgrade of lubuntu as ubuntu was just too slow because of low power graphics...
now, i have no audio, the sound icon wont open.
i have installed alsa mixer

i can connect as headset device ok, i cant connect as audiosink - stream setup failed...



well i hope someone has some good tips for me to try :)
thanks in advance, Ian, M6YRU

---

### Post by 6-launchpad-net-cefn-com on 2014-12-06
In Lubuntu 14.04 I had the same problem after installing blueman and finding an audio output and trying to connect; "Connection Failed: stream setup failed"  I installed packages like this...sudo apt-get install blueman pulseaudio pulseaudio-module-bluetooth pavucontrol...and after a restart I could load the module with...
sudo pactl load-module module-bluetooth-discover
...launch blueman, search for an audio output and connect successfully. Launching Pavucontrol I could then switch outputs.

---

