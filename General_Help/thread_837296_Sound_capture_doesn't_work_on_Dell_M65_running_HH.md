---
title: "Sound capture doesn't work on Dell M65 running HH"
date: 2008-06-22
forum: General Help
---

### Post by dhiman on 2008-06-22
The sound capture on my Dell M65 stopped working when I switched from 7.xx to 8.xx. The playback works ok.  So, if I call someone using Gizmo, for example, I can hear that person but he can't hear me.
I tried

> arecord -l
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

But when I go "Syetem" -> "References" -> "Sound" and click the "Test" button next to  "Sound capture", an error message pops up saying "Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile = chat'

Any idea on how to fix this?

Thanks,
Dhiman

---

