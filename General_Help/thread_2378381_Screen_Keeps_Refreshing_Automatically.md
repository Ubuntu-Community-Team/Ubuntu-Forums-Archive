---
title: "Screen Keeps Refreshing Automatically"
date: 2017-11-22
forum: General Help
---

### Post by kamrynborden on 2017-11-22
On one of my computer, today, I noticed that the screen decorations (top bar and side bar would disappear and reappear again. It seems to happen randomly very frequently and when I click on any the ions on the side bar, it'll trigger it, and nothing else would happen until the third time I click on an icon. I've never seen it before. Everything on the screen will disappear (except the wallpaper and mouse pointer) and reappear again. Sometimes it'll freeze for a few seconds before it happens. The super key triggers it every time.

Computer specs:
OS: Ubuntu 16.04 x64
Motherboard ASUS P5QPL-VM EPU
Processor: Pentium(R) Dual-Core CPU E5400 @ 2.70gb x2
Graphics: Intel G41 (Integrated)
RAM: 2GB DDR2 @ 800MHz (x2)
Drive: Silicon Power 120GB SSD (SATA)
Monitor: ASUS VS228H-P (HDMI) @ 1920x1080

---

### Post by kamrynborden on 2017-12-06
I'm pretty sure it has to do with Compiz. I reinstalled and it happens right after I enable the 'Negative' setting. If I take the drive out and put it in another computer, it doesn't do that. I started happening last month. It makes it nearly impossible to use becuase it'll go out and show the log in menu as soon as I put my mouse near the right-side or press the Super key.

---

### Post by kamrynborden on 2017-12-09
Bump

---

### Post by again? on 2017-12-09
The negative effect is part of the compiz-plugins package which isn't officially supported by Ubuntu.
Plugins from this package may occasionally break as Ubuntu's compiz is updated.

---

### Post by kamrynborden on 2017-12-15
Update: I installed Ubuntu 17.10 on a laptop, a HP Elitebook, and it does the same thing. It was as soon as I clicked on Unity, and didn't do anything in compiz on that one. It appears to be the Unity package. I will check for a PPA and try that and let you know how it goes.

---

### Post by kamrynborden on 2017-12-18
I seemed to have fixed it on one computer. I disabled the 'Gnome Compatibility' in Compiz, but that doesn't work for the laptop.

---

