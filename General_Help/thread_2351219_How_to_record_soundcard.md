---
title: "How to record soundcard?"
date: 2017-02-01
forum: General Help
---

### Post by frank2222 on 2017-02-01
Could someone please recommend a program to save the sounds going through my soundcard?
Trying to use a combination of mic sounds mixed with saved sounds...
Ubuntu 16.04

Thanx in advance

---

### Post by howefield on 2017-02-01
Audacity ?

Run Audacity with default settings start recording, then run pavucontrol, go to Recording tab and change ALSA plug-in [audacity] : ALSA Capture from - to Monitor of Built-in Audio Analogue Stereo.

---

### Post by ajgreeny on 2017-02-01
Or have a look at  audio-recorder from the ppa at [https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa](https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa) which is a much smaller and simpler application than audacity.

I use both quite a lot, but generally use audacity for editing sound rather than just recording, but it depends how much recording control I need, as audacity is a lot more flexible than audio-recorder.

---

### Post by frank2222 on 2017-02-02
Thank you for taking the time to reply. I will check them out.

---

