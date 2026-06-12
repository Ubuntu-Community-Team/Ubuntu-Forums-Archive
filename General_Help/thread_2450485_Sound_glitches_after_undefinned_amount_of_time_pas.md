---
title: "Sound glitches after undefinned amount of time passes."
date: 2020-09-14
forum: General Help
---

### Post by mynameisvkt on 2020-09-14
My sound ends up glitching if I don't restart every so often. Sometimes it'll glitch after an hour, sometimes after 2 minutes. I haven't had this issue in the past. I used to be on arch and it was fine for a while, until one day I started having this issue. I changed to ubuntu, and I still have this problem. I only have this issue on linux so the issue is in my software and not my hardware.
Below is an audio recording of my speakers.
[https://drive.google.com/file/d/1M0YrUUrOn-ffnfcU5CyC-JaPDlBZh0Qp/view?usp=sharing](https://drive.google.com/file/d/1M0YrUUrOn-ffnfcU5CyC-JaPDlBZh0Qp/view?usp=sharing)

---

### Post by TheFu on 2020-09-15
Have you tried restarting pulseaudio?
```
pulseaudio -k
pulseaudio &
```
May need to close any applications connected to the old instance.  Chromium (and all chromium-based browsers) seem to cause the problem, IME.

---

