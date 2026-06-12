---
title: "Sound output to headphones not working"
date: 2013-01-09
forum: General Help
---

### Post by Alan.Brown on 2013-01-09
I am using Xubuntu 12.10 fully updated on an HP 200-5220a.   I have a Hi-Fi system plugged into the headphones output.  This has worked without any problems for nearly two years until the last 2 or 3 days.   Then the sound output stopped.  I think I may have reset something somewhere!

I can correct the problem by going into the **Menu > Multimedia > PulseAudio Volume Control**.   Under the **Output Devices** tab the **Port** setting shows "**Speakers**"   If I change this to **"Headphones"** everything works OK as expected.

Problem is that this setting change does not get saved and shows **"Speakers"** again after I reboot.   I then need to reset it each time.   I have looked for settings files for PulseAudio but cannot find them.  I have tried **Settings Manager > Save Session** but the setting is still not saved.

Please help

TIA

Alan

---

### Post by Alan.Brown on 2013-01-09
Solved!  I went into **Menu > Multimedia > GNOME ALSA Mixer** (***gnome-alsamixer ***from the terminal) and ticked the **"Speaker"** box.  Also made sure the **"Master"** and **"Headphones"** boxes were unticked (ie un-muted).   This fixed the problem even after a reboot.

This may help others with similar problems

---

