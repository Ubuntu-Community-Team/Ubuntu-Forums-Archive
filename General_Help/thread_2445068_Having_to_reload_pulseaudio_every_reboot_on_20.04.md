---
title: "Having to reload pulseaudio every reboot on 20.04"
date: 2020-06-08
forum: General Help
---

### Post by f00dl3 on 2020-06-08
Ever since upgrading to Ubuntu 20.04 LTS in late April, after every reboot if I go straight into settings the Output Device is set to Dummy Output and Input device is blank. If I try to play audio, it goes to my HDMI monitor. Only after doing a pulseaudio -k && sudo alsa force-reload does Line Out - Built-in Audio "magically" show up in the Output Device field. 

Is this a known issue or is it unique to me?

---

### Post by ActionParsnip on 2020-06-09
What did you upgrade from?
What method did you use?
If you add a startup item that runs those commands, is it OK?

---

