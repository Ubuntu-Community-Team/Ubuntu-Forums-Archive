---
title: "Sound stopped working"
date: 2008-05-28
forum: General Help
---

### Post by pylon42 on 2008-05-28
Hokay, my sound stopped working randomly...

I'm trying to reinstall the alsa drivers, but I need to stop snd_hda_intel

This worked 2 weeks ago, but now it doesn't:

kill $(lsof -t /dev/dsp* /dev/snd/*) &&
   sudo modprobe -r $(lsmod |grep ^snd |awk '{print $1}') &&


Isn't there some simple command like "kill snd_hda_intel"?

If you're thinking "He can't possibly be asking such a simple question... there must be more to this", I can assure you there isn't and I am.

---

### Post by Plasma_NZ on 2008-05-29
Okay

How many soundcards do u have ? do u just have onboard ? or do u also have a PCI card.?

---

### Post by johwel on 2008-05-29
Pylon42, do u by any chance dual boot with Windows, and is the sound off after rebooting from Windows to Ubuntu?

---

### Post by pylon42 on 2008-05-29
Just one soundcard, in a lenovo x300, no dual boot.

Sound doesn't work by default in Hardy, but I've gone through a process to fix it several times successfully. Never had a problem until that script stopped working that allowed me stop stop snd_hda_intel.

I can't install the new alsa driver while it's running...

---

### Post by pylon42 on 2008-05-30
Let me rephrase this:

Is there any way to stop a process in ubuntu?

For example, in Windows I would hit "ctrl+alt+del", select "hda_snd_intel" and end the process.

---

