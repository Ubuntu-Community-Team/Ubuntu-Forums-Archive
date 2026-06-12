---
title: "How to restart the audio system completely?"
date: 2008-05-17
forum: General Help
---

### Post by descentspb on 2008-05-17
I have a bug sometimes with pulseaudio. It says that the device is busy and any App that uses pulse does not have any sound. The ones that are using just alsa are playing fine.

"sudo /etc/init.d/pulseaudio restart" does not help.

If i do "sudo rmmod snd_hda_intel" it says that the module is busy. I want to do it without "init 1; init 2"

Thanks!

---

### Post by descentspb on 2008-05-19
bump

---

