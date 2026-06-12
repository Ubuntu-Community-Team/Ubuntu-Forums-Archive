---
title: "Audacity, Pulse and Ubuntu"
date: 2024-02-14
forum: General Help
---

### Post by Tristan57 on 2024-02-14
Hi there, I am running Audacity 3.1.3 in Ubuntu 22.04.3 LTS. I want to  record from the web and noticed that I needed PulseAudio - which I have  installed. However, Audacity doesn’t see it and Pulse doesn’t see  Audacity either. Help please, and thank you.

---

### Post by Holger_Gehrke on 2024-02-15
Since the standard candidate for installation on Ubuntu 22.04 through apt is version 2.4.2 while snap will install the version you have, you've probably installed a snap of audacity. Applications installed through snap are constrained in various ways and can't see or use parts of the normally installed system unless expressly allowed to do so and the author of the snap prepared the snap to use that permission. You could try 'snap connect audacity :pulseaudio' (or some variation of that; read 'man snap' for details). If that won't work, you could remove the snap ('snap remove audacity') and install audacity through apt ('sudo apt install audacity').

Holger

---

### Post by tea for one on 2024-02-15
I have the deb version of Audacity (good advice from Holger)

After you have installed Audacity (deb version)
```
sudo apt install audacity
```
Install pavucontrol 
```
sudo apt install pavucontrol
```
Navigate to your chosen website and play some sound
Open Audacity and press Record
Open Pavucontrol
Open Recording tab
Switch to Monitor of your sound (HD Audio, Headphones, Bluetooth etc.)
Audacity should now be recording &#8220;What you hear&#8221;
Screenshot attached

---

