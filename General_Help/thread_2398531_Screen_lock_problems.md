---
title: "Screen lock problems"
date: 2018-08-13
forum: General Help
---

### Post by hardcoretexan on 2018-08-13
I have a new Dell inspiron  with windows 10 and dual boot with 18.04 Ubuntu and my screen locks everytime I restart or sign off. I have the screen lock turned off under the privacy settings tab but it still locks and since I am the only one using this computer I don't want it to lock unless I want it to.

AMD Ryzen&#8482; 3 2200U Mobile Processor with Radeon&#8482; Vega3 Graphics
12GB, DDR4, 2400MHz,
Dual Boot Windows 10 Home 64-bit/Ubuntu 18.04.1 LTS

---

### Post by hardcoretexan on 2018-08-14
Has anyone any ideas???

---

### Post by #&amp;thj^% on 2018-08-14
see if this is any different:
```
gsettings set org.gnome.desktop.screensaver lock-enabled false
```

---

