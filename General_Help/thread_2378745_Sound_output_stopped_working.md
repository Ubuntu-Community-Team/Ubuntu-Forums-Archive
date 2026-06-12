---
title: "Sound output stopped working"
date: 2017-11-26
forum: General Help
---

### Post by jason13 on 2017-11-26
My line out to a set of speakers has stopped working and I can't figure out why. Here's what I've tried so far: The speakers still work by using the radio. The computer will output sound over the HDMI connection to a monitor. The headphone jack also has stopped working. I've power cycled both the stereo and the computer, checked all the wire connections between the computer and the speakers to no avail. How can I figure out what's gone wrong?

---

### Post by uRock on 2017-11-26
Open System Settings > Sound > then select the output method.

---

### Post by jason13 on 2017-11-26
That was the first thing I did. I've also confirmed the connecting cable is good by hooking it up to an external sound source. I did just install a bunch of Ubuntu updates, that's the only other recent change I'm aware of.

---

### Post by jason13 on 2017-12-01
Bumping this because I'm ready to reinstall the OS and not looking forward to it, I haven't been able to figure anything else out.

---

### Post by Yellow Pasque on 2017-12-02
Try resetting the user's pulse configuration so a fresh one gets generated:
```
rm -r ~/.config/pulse; pulseaudio -k
```
If that doesn't help, give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by maglin2 on 2017-12-02
Have you installed firejail? I ask because that happened to me after I installed firejail. If so the fix is here [https://sites.google.com/site/easylinuxtipsproject/sandbox](https://sites.google.com/site/easylinuxtipsproject/sandbox)
Just a thought - I note that you said you had done noting but updates recently though.

---

