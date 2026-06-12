---
title: "Multitouch and Headphone White Noise on Asus Zenbook Pro UX501VM with Ubuntu 16.04"
date: 2016-10-17
forum: General Help
---

### Post by nofilefound on 2016-10-17
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]I have installed Ubuntu on my Asus Zenbook Pro UX501VM and I have two problems : I've partly fixed the headphone noise and I have no clue for the touchpad    I can't use 2 finger scolling and other mutitouch tasks.I have fixed the headphone noise temporary by changing a confing in **/etc/modprobe.d/alsa-base.conf** i have added this line :
```
options snd-hda-intel model=dell-headset-multi

```But when I close my laptop and reopen it the noise comes back. Even if I restart alas and pulseaudio.
My kernel version is **4.6.0-040600-generic** (i have tried 4.3.5 but the computer won't boot anymore).
I don't know if it helps but I have nvidia drivers.
Thanks for your help.
    
[/TD]
[/TR]
[/TABLE]

---

