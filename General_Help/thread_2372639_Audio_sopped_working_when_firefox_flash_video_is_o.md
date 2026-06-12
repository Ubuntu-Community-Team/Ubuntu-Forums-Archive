---
title: "Audio sopped working when firefox flash video is open"
date: 2017-09-27
forum: General Help
---

### Post by jimhce on 2017-09-27
Hi,

I am running 14.04.5, the audio is working fine, but as soon as the firefox flash video is open, the firefox flash video can play both video / audio, but the system audio was no long working, there was no sound from test audio on top of the audio setting menu. Has anyone knows why and how to fix it?

Thank you.

Kind regards,

---

### Post by ajgreeny on 2017-09-27
With FF running and a flash video playing open pulseaudio-volume-control (Sound-Settings from the volume icon in panel will get you there) and see what is showing in the Output Devices tab.

It should show the Firefox output and allow you to set the volume level of that separately from any other output devices.

---

### Post by jimhce on 2017-09-28
Change to Chromium, the problem is gone.

---

