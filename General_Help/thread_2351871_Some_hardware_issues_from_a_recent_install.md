---
title: "Some hardware issues from a recent install"
date: 2017-02-07
forum: General Help
---

### Post by narev2 on 2017-02-07
I have Ubuntu 16.04 on an old computer I needed to totally wipe as it was rife with viruses. I love it, but can't get it to see the 3d card, a Radeon 9500, or the new mouse and speakers I purchased. I don't know that the audio card works either, I've never heard a peep. I tried following the instructions on AMDs site, and it was a disaster, I couldn't log in. I'd like to get this working, but also learn what I'm doing and why. If I just cut and paste commands, I might as well be Windozing. I really want my games to work, especially Diablo 3 and World of Warcraft. If I can do that, it'll be Ubuntu 4 life!

---

### Post by Perfect Storm on 2017-02-07
I'm no radeon expert but [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) suggest that you install xserver-xorg-video-amdgpu for your card

> Unsupported chips
Ubuntu 16.04 LTS and newer: for some most recent cards (R9 285, R9 380/380X, R9 M395X, R9 Nano, R9 Fury/FuryX and so on), the open-source AMDGPU driver is enabled by default. For Ubuntu 16.04 LTS if you have the very latest Radeon RX 4xx graphics cards, AMDGPU-Pro hybrid driver is available to download here (please read the release notes for known problems and limitations).

Previous release: for the very latest cards, open-source driver support is not always instant, using proprietary fglrx/Catalyst driver may be necessary. In this case, read this page. 
If you have Ubuntu 14.04 LTS with Linux kernel 4.4.0 (HWE stack Xenial), you can't install the proprietary fglrx/Catalyst driver. However the open source AMDGPU driver is available to install through the xserver-xorg-video-amdgpu package.


For your sound problem please run though this list: [https://help.ubuntu.com/16.04/ubuntu-help/sound-nosound.html](https://help.ubuntu.com/16.04/ubuntu-help/sound-nosound.html) if that didn't help check out: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

