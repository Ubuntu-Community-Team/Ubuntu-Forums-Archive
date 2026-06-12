---
title: "No voice sound with skype and ubuntu 12.04"
date: 2013-08-23
forum: General Help
---

### Post by MgFrobozz on 2013-08-23
Skype was working ok until an apt-get update two days ago. After the update, folks that I'm calling (either on another computer, or on a land line) have been able to hear me, but I've been unable to hear them. My audio system works well for every other application, and I can hear the skype sound effects (like the generated ringing when calling, and the "bloop" when the call ends), but I can't hear any voices, including that on the "Skype Test Call". 

I fired up WindowsXp running under vmware on the same system (ubuntu 12.04.2), and skype running on winxp works properly. This is using the same hardware, but a slightly different path to the audio driver via the vmware drivers. 

Any ideas on how to debug this will be greatly appreciated ... 

```

> skype --version
Skype 4.2.0.11
Copyright (c) 2004-2013, Skype

> cat /etc/lsb-release 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"

> uname -r
3.2.0-52-generic

```

---

### Post by MgFrobozz on 2013-09-12
I tried the following, in order to remove and re-install skype ...

```
sudo apt-get remove skype
sudo apt-get autoremove
sudo apt-get install skype
```

... but no change (sound transmission from my system ok, to my system is broken). The options mentioned controlling volume with "PulseAudio volume control", so I did this ...

```
sudo apt-get install pavucontrol
```

... after which there was no sound at all from skype or any of my other applications. So I ran ...

```
sudo apt-get remove pavucontrol
```

but all sound (mike and speakers) is still dead.

---

### Post by MgFrobozz on 2013-09-13
Sound was still working ok with the other accounts. In SystemTools/SystemSettings/Sound, I found that my default output had changed from "Built-in Audio Analog Stereo" to "RS880 HDMI Audio [Radeon HD 4200 series] Digital Stereo (HDMI)". I think the latter is on my Hauppauge video card.

Switch it back to analog output, now it's ok.

---

