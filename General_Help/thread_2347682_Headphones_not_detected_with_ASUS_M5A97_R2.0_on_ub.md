---
title: "Headphones not detected with ASUS M5A97 R2.0 on ubuntu 15.04"
date: 2016-12-27
forum: General Help
---

### Post by cgameing on 2016-12-27
My headphones arent detected in alsa (or whatever the default ubuntu settings for sound is called)
I have a r7-240
A fx-6300
and a Asus M5A97 R2.0

My sound used to work, but I think a update might have come out that broke my ability to use headphones as a audio device. Because I tried 2 fresh installs to see if it would work and it does work but when I run sudo apt-get upgrade, it breaks it and I can nolonger detect it.
My headphones are detected in Alsamixer but unmuting them by clicking m and putting them to full volume does nothing.

lspci -nnk | grep -iA2 audio    gives:
```
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8444]
    Kernel driver in use: snd_hda_intel
--
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series] [1002:aab0]
    Subsystem: ASUSTeK Computer Inc. Device [1043:aab0]
    Kernel driver in use: snd_hda_intel
```

I don't think its a hdmi issue either, because only using vga doesnt fix the issue.

This Forums solution dident work for me
[http://askubuntu.com/questions/132440/headphone-jack-not-working](http://askubuntu.com/questions/132440/headphone-jack-not-working)

I am getting fairly similar symptoms as this guy, but the solutions seem to be gigabyte specific:
[http://askubuntu.com/questions/620405/audio-playing-on-headphones-and-speakers-ubuntu-15-04](http://askubuntu.com/questions/620405/audio-playing-on-headphones-and-speakers-ubuntu-15-04)[URL="http://askubuntu.com/questions/620405/audio-playing-on-headphones-and-speakers-ubuntu-15-04"]


Thanks for any help
[/URL]

---

