---
title: "Play music from laptop to bluetooth on my crosley turntable"
date: 2017-08-22
forum: General Help
---

### Post by giel2 on 2017-08-22
Dear sir/madam,

I would like to play my mp3 files (they are on my xubuntu 16.04 laptop) on my bluetooth enabled turntable (crosley cruiser deluxe).

When I open my bluetoothmanager in xubuntu I see the device in the list. I can connect with the device, and choose setup, trust and audiosink). However when I play music it keeps coming from my laptop speakers (very bad sound quality i fear).

When I use my iphone to play music to the crosley turntable, it works flawlesly.

Does anyone know what I should do to make this work? I already did apt-get update/upgrade

Best regards,

Giel

---

### Post by ajgreeny on 2017-08-22
You may need to use pulseaudio-volume-control (Sound Settings from the volume panel icon) to mute the internal speakers, which I presume will not affect the volume through bluetooth, though b/t is not something I use, so I hope I am correct about that.

---

### Post by giel2 on 2017-08-23
Yes that was it: I had to manually disable the internal speakers in the sound settings. Thanks!

---

