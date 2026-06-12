---
title: "No audio after Samba install (Ubuntu 15.10), &quot;Dummy Output&quot; Device listed instead"
date: 2015-11-18
forum: General Help
---

### Post by Willem_Hillier on 2015-11-18
My audio has worked fine for around three months now, and then I installed Samba. Usually, under the "Sound" settings, three devices are listed: my video card's HDMI port, analog surround, and the optical output on my computer. After installing Samba, suddenly I only have a "dummy" device listed. Over the past couple of days, I have tried several other threads on problems like this. I have completely re-installed pulseaudio and alsa-base, to no avail. The really weird thing is that alsamixer detects my devices.

Any help would be greatly appreciated! And a warning: I have only been using Ubuntu for around three months. Don't let this scare you! I have the basics of the terminal under my belt!

---

### Post by Willem_Hillier on 2015-11-18
For anyone interested, I just solved my own problem! Somehow my /etc/asound.conf file was corrupted. I deleted it, and then re-created it, and now everything works wonderfully!

---

