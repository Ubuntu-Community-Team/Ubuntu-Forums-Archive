---
title: "Pulseaudio failed to create secure directory"
date: 2021-09-07
forum: General Help
---

### Post by tommyfun on 2021-09-07
I have a lab of 20.04 desktops using nis and autofs mounted nfs home directories and the audio doesn't work.

pulseaudio[5214]: Failed to create secure directory (/home/username/.config/pulse): Operation not permitted
systemd[5121]: pulseaudio.service: Main process exited, code=exited, status=1/FAILURE
systemd[5121]: pulseaudio.service: Failed with result 'exit-code'.
systemd[5121]: Failed to start Sound Service.

pulseaudio doesn't seem to be able to write to the nfs mounted home directory.

My fedora 34 workstations work just fine, they use pipewire.

please help,
-tom

---

