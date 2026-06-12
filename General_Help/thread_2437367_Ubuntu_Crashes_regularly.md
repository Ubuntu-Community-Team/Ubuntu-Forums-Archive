---
title: "Ubuntu Crashes regularly"
date: 2020-02-22
forum: General Help
---

### Post by archimedes1981 on 2020-02-22
I built a Ryzen 3 2200G system a while back and I rarely use it but when I do it practically always crashes. 
I'd like to solve it but I lost touch with linux for a while and am sort of lost at the moment.
I opened the logs but couldn't figure out anything.
Anybody can help?
At the moment it freezes everytime I shoot the same guy in Tomb Raider. I don't thinik it's the game because it also freezes while youtube is playing.
Might be graphics related. I only use the Vega graphics on chip and have no overclocking or weird settings. I also just updated the bios for my mobo Which is an ASUS B350M-A.
Any help really appreciated. Please be specific because I reverted to noob level here.

---

### Post by thehipho on 2020-02-23
Does this happen often or only during high CPU? 
Test with another OS, to eliminste hardware issues?
Post output of sensors:
```
sudo apt install lm-sensors
sensors-detect
sensors

```

---

