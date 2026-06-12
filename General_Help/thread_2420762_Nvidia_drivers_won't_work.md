---
title: "Nvidia drivers won't work"
date: 2019-06-10
forum: General Help
---

### Post by andreij5 on 2019-06-10
Hello, I'm having a hard time with my graphics-card drivers: They worked well for a long time, until eventually (probably after an update, but it was some time ago) I had issues with unmet dependencies related to the proprietary nvidia driver (libnvidia-ifr1-390, libnvidia-ifr1-390:i386, nvidia-driver-390). Everything continued to work well (for example I could play Civilization V), but I couldn't update or install anything anymore. So I unistalled the drivers (using apt-get purge nvidia*) and tried to reinstall them. I tried a lot of methods, for example with "Software and Updates" from the GUI or "ubuntu-drivers autoinstall" or "apt-get install nvidia-driver-390" etc. Most of the times the installation seems to work (like the general GUI is fine), but when I try to start the previously working game it fails to load. I'm quite a noob, so I uite sure I'm doing something wrong. Can anyone tell me what exactly? The graphics card is an old NVIDIA GeForce GT 540M and i run UBUNTU 18.04.2 LTS.

---

### Post by oldrocker99 on 2019-06-10
Try this:```
sudo apt remove nvidia*
sudo apt-add-repository ppa:graphics-drivers/ppa
```      (it should automatically update)
```
sudo apt install nvidia-driver -390
```

Reboot, and you'll be set. One of the very few times when you **have** to reboot.

---

### Post by andreij5 on 2019-06-10
Thanks for the suggestions. I'm quite sure that I had already tried that, but just to be sure i did it again. Unfortunately no real improvement, the installation seems to be good, and the display works correctly, however I still cannot start games.

---

### Post by dino99 on 2019-06-10
do you see warnings or errors via 'journalctl -b' into a terminal and a rescue session ?

---

### Post by andreij5 on 2019-06-10
Possibly?
```

Jun 10 18:46:27 andreij-RC530-RC730 nvidia-settings-autostart.desktop[1950]: ERROR: NVIDIA driver is not loaded
Jun 10 18:46:27 andreij-RC530-RC730 nvidia-settings-autostart.desktop[1950]: ERROR: Unable to load info from any available system
Jun 10 18:46:27 andreij-RC530-RC730 gsd-color[1416]: failed to set screen _ICC_PROFILE: Failed to open file “/home/andreij/.local/share/icc/edid-97b7a4b585ab50999a1e339bee5c5e47.icc”: Permission denied

```
I out the full output here: [Link]("https://paste.ubuntu.com/p/PMwnZ5wbwN/")

---

