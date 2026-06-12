---
title: "Intermittent sound playing"
date: 2008-05-01
forum: General Help
---

### Post by Greenery on 2008-05-01
I've been having problem with my sound on my Kubuntu recently after my upgrade (not fresh install) to Kubuntu 8.04; the sound is playing intermittently. I followed the General Help guide from [this](https://help.ubuntu.com/community/SoundTroubleshooting) and it still doesn't work.

Any ideas?

---

### Post by elvinatom on 2008-05-01
Seems to be the wrong guide for your problem. I had crackling sound issues in games and got them resolved like this:
```
sudo apt-get install libsdl1.2debian-oss
```
That will remove "libsdl1.2debian-alsa", so if you wanna undo it type:
```
sudo apt-get install libsdl1.2debian-alsa
```
But it helps with alsa buffer underruns only (at least I think it does).

---

### Post by cszikszoy on 2008-05-01
Can you post any relevant messages from the syslog.  I was having problems with pulseaudio, and found a bunch of errors from it in the syslog.  My problems were fixed by using ALSA for all sound output options (not sure where it is in kubuntu, I have ubuntu).

---

### Post by Greenery on 2008-05-05
> **cszikszoy said:**
> Can you post any relevant messages from the syslog.  I was having problems with pulseaudio, and found a bunch of errors from it in the syslog.  My problems were fixed by using ALSA for all sound output options (not sure where it is in kubuntu, I have ubuntu).

I did fresh install of Kubuntu and the intermittent sound playback is still happening. I checked KSysLog and I don't see errors with respect to sound. Maybe I'm not looking at the SysLog correctly.

Can a defective speaker cause the intermittent sound problem? I didn't have this problem in Kubuntu 7.10 before and I still dual boot with Windows and my speaker has no problems with exception that the subwoofer keeps plugged in and out according to my RealTek HD Audio manager at times.

---

