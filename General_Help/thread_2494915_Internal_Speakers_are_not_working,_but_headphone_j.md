---
title: "Internal Speakers are not working, but headphone jack is working fine, with Realtek A"
date: 2024-01-31
forum: General Help
---

### Post by suriocity on 2024-01-31
Recently  I bought Infinix Y4 Max laptop and replaced the preinstalled Windows  with kubuntu 22.04. Everything is working fine except the internal  speaker (also fast charging is not happening but that's not much of an  issue) but audio is working fine from headphone jack. The codec is **Realtek ALC269VC** but It shows **Speakers (unavailable)** in audio settings. Currently it's on **Linux 6.5.0-15-generic x86_64** kernel. I used **alsamixer** to change volume and mute/unmute and **hdajackretask**  to change unconnected pins or whatever that is, still no success. I  googled and check many pages related to this codec but no solution  helped in my case. Would could be the reason for this issue? speaker  worked fine in windows tho.

  all the system information is in this link. [https://termbin.com/mhzu](https://termbin.com/mhzu)

---

### Post by suriocity on 2024-01-31
**Partially solved **

After going through this page. ([https://www.kernel.org/doc/html/latest/sound/hd-audio/models.html](https://www.kernel.org/doc/html/latest/sound/hd-audio/models.html))  and some trial and error and I find out that adding **options snd_hda_intel model=dell-inspiron-7559** at the end of **/etc/modprobe.d/alsa-base.conf** works better for my laptop. The internal speakers are working now but the headset microphone are not. I tried many model code and figure out that with **alc288-dell1**, **alc288-dell-xps13**, **alc298-dell1** and **alc298-spk-volume**, the headset microphone are working but internal speakers are not. So either internal speaker will work or headset microphone.

---

### Post by traxbee on 2024-02-16
Update: suriocity's  tweak working Thanks .it was my typo error.
and also headphone/speaker switching properly

---

