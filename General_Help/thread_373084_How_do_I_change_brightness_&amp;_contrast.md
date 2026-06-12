---
title: "How do I change brightness &amp; contrast?"
date: 2007-02-28
forum: General Help
---

### Post by daffy on 2007-02-28
Hello,
In WinXP I have a utility to change (for example) the brightness, contrast, gamma on my nvidia gfx card. In ubuntu I only find a way to change the gamma by editing xorg.conf. How do I change the contrast & brightness for an Nvidia graphics card in ubuntu? Im currently using the latest drivers from nvidia.

Thank you in advance,
/D

---

### Post by 23meg on 2007-02-28
If you're using the proprietary driver, launch the X server settings app (in Applications / System Tools). You'll find the settings under "X Server Color Correction".

---

### Post by daffy on 2007-02-28
Aha.. I am using the proprietary driver, but am on a *very* stripped down system (automatically starts a single app when X is loaded). Can I install (if not already installed) and run this app "standalone"? If so, what is the package name?

Thank you for you fast reply!
/D

---

### Post by 23meg on 2007-02-28
If you have the proprietary driver, you have the app in "/usr/bin/nvidia-settings". You don't have to separately install it.

---

### Post by daffy on 2007-02-28
Wonderful!

Thanks for the help =)

/D

---

