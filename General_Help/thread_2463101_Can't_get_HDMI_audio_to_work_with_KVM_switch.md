---
title: "Can't get HDMI audio to work with KVM switch"
date: 2021-06-03
forum: General Help
---

### Post by ccrs8 on 2021-06-03
To help with my work-from-home setup, I recently purchased and set up this KVM:
[https://www.amazon.com/TESmart-Monitor-Switch-Updated-Support/dp/B083MZSVFM/](https://www.amazon.com/TESmart-Monitor-Switch-Updated-Support/dp/B083MZSVFM/)

I'm having problems getting audio working on my personal Xubuntu 20.04 Intel Nuc8.  It worked out of the box with my work Windows 10 machine.  Both machines are hooked up to the KVM with HDMI cables, and then there is a 3.5mm audio output jack on the KVM itself that goes to my speakers.  With my Widows laptop, sound immediately started playing out of my speakers.  With my Xubuntu machine, it is silent.  All HDMI entries in the list of profiles for my built-in audio show "(unplugged)(unavailable)" next to them.

If I hook up my personal machine to a television via HDMI using the exact same cable, sound comes out of the TV right away, so I don't think it's an issue with HDMI itself or the cable.  Does anyone have any experience with this type of setup?

---

### Post by dddman on 2021-06-03
I may of hit on something

[https://askubuntu.com/a/1315581](https://askubuntu.com/a/1315581)

---

### Post by ccrs8 on 2021-06-03
> **dddman said:**
> I may of hit on something

[https://askubuntu.com/a/1315581](https://askubuntu.com/a/1315581)

Unfortunately, none of the profiles are NOT marked as unavailable/unplugged in that drop-down.

Another thing I tried was adding the line:
```
options snd-hda-intel model=generic
```
to /etc/modprobe.d/alsa-base.conf

While that significantly reduced the entries in that drop-down AND removed the "(unavailable)" from the "Digital Stereo (HDMI) Output" entry in that list, it did not actually produce sound.

---

