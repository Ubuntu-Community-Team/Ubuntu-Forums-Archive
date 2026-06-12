---
title: "Line Out MISSING!"
date: 2023-04-30
forum: General Help
---

### Post by KDMerrill on 2023-04-30
Help!  Running Ubuntu 22.04 on a G31-P21 motherboard.   Installed OpenShot last week to dabble with video editing and when I did my audio stopped working.

Upon further inspection,  when looking at Options - Sound;  my Audio Line Out option has vanished, leaving my only audio out device 'Digital Output (S/DIF)'.

Does anyone know what config files I can edit to restore my 'Audio Line Out' as a valid output device?? I use a set of Bose speakers plugged into the audio line out...and I REALLY miss having sound!!!

Kevin in VA

---

### Post by idmbe on 2023-04-30
For 22.04 see this:
[https://manpages.ubuntu.com/manpages/jammy/man5/pulse-daemon.conf.5.html](https://manpages.ubuntu.com/manpages/jammy/man5/pulse-daemon.conf.5.html)

Also look at that maybe will helpful for you: 
[https://askubuntu.com/questions/1317884/how-to-configure-the-default-sound-output-device](https://askubuntu.com/questions/1317884/how-to-configure-the-default-sound-output-device)

---

