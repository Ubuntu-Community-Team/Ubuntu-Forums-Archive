---
title: "I'm having a sound issue."
date: 2014-08-08
forum: General Help
---

### Post by MrOstrichman on 2014-08-08
I have recently installed Ubuntu 14.04 alongside Windows XP on an old Dell Dimension 4600. I cannot get sound to play when in Ubuntu. I know it is not a hardware issue because Windows plays sound just fine. It is also not just a bug in my copy of Ubuntu because I have download and loaded another copy of Ubuntu from a USB. I have looked everywhere I know to look and have not found a solution. Thanks in advance.

---

### Post by Rev2010 on 2014-08-08
In my experience it's usually happened to me when I install Ubuntu on systems that also have HDMI audio output and such (ATI Radeon cards for example have this). I've had to manually switch to the actual soundcard and not the audio included on the video card since Ubuntu has often defaulted to the HDMI audio output. Go into System Settings -> Sound. Under the Output tab what do you have listed?


Rev.

---

### Post by MrOstrichman on 2014-08-08
[SIZE=2]It has two options:

Analog Output/No Amplifier[/SIZE]
*Built-in Audio*

and

Analog Output/Amplifer
*Built-in Audio*

---

### Post by Rev2010 on 2014-08-08
If you try selecting the second one, the one that's not already selected, do you still not have any sound? 

Rev.

---

### Post by MrOstrichman on 2014-08-09
There is no sound for the second option.

---

### Post by Jesse_Campton on 2014-08-09
Open a terminal> type alsamixer <press enter> > use your arrow keys to scroll through and make sure all your volumes are turned up.. just a thought..

---

### Post by MrOstrichman on 2014-08-10
> **Jesse_Campton said:**
> Open a terminal> type alsamixer <press enter> > use your arrow keys to scroll through and make sure all your volumes are turned up.. just a thought..

That did nothing.

---

### Post by FriedMicro on 2014-08-10
Try this in a terminal:
```
aplay /usr/share/sounds/alsa/Front_Center.wav
```

If that fails try this (you'll be prompted for your password
```
sudo aplay /usr/share/sounds/alsa/Front_Center.wav
```

This will install the proprietary sound drivers:
```
sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
```

I got this from:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by MrOstrichman on 2014-08-11
> **FriedMicro said:**
> Try this in a terminal:
```
aplay /usr/share/sounds/alsa/Front_Center.wav
```

No sound played.

> **FriedMicro said:**
> If that fails try this (you'll be prompted for your password
```
sudo aplay /usr/share/sounds/alsa/Front_Center.wav
```

No sound played.

> **FriedMicro said:**
> This will install the proprietary sound drivers:
```
sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
```


I recieved this message:

E: Unable to locate package linux-restricted-modules-3.13.0-32-generic
E: Couldn't find any package by regex 'linux-restricted-modules-3.13.0-32-generic'

---

