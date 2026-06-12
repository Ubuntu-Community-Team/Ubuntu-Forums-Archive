---
title: "Sound coming from laptop internal speakers, not HDMI"
date: 2023-01-12
forum: General Help
---

### Post by john163 on 2023-01-12
Ubuntu 20.04.5  I have it set to do nothing when the laptop lid is closed  Laptop is Dell Latitude E7440  HDMI out is connected to a TESmart KVM switch.  Issue is, even when the sound control panel is set to HDMI, sound comes out the internal speakers in the laptop.  Googling turns up a bunch of ten year old results for ancient versions of Ubuntu.  Trying to kill pulseaudio, clear related files, restart, etc. doesn't help.

---

### Post by MAFoElffen on 2023-01-13
What device does it say is active in Settings > Sound > Output > Output Device ?

---

### Post by john163 on 2023-01-13
> **MAFoElffen said:**
> What device does it say is active in Settings > Sound > Output > Output Device ?

[IMG]http://www.sdsitehosting.net/jnojr/u.png[/IMG]

---

### Post by ActionParsnip on 2023-01-13
If you install and use pavucontrol, does it help?

---

### Post by john163 on 2023-01-13
> **ActionParsnip said:**
> If you install and use pavucontrol, does it help?

I guess not.  I installed it and ran it.  It gives me a different GUI, but I don't see any settings that look relevant. Tested again, sound is still coming from internal speakers.

---

### Post by john163 on 2023-01-13
And, FWIW, I tested with the monitor attached directly to the laptop.  Same thing, so it isn't the KVM.

---

### Post by john163 on 2023-01-13
joliver@blinky:~$ pactl list short sinks
1    alsa_output.pci-0000_00_1b.0.analog-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
4    alsa_output.pci-0000_00_03.0.hdmi-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED

---

### Post by john163 on 2023-01-13
Fixed it!  In /etc/pulse/default.pa I commented out :
load-module module-suspend-on-idle

---

