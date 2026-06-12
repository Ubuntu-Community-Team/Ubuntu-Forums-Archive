---
title: "Ubuntu/Kbuntu can I start again?"
date: 2006-08-17
forum: General Help
---

### Post by siherts on 2006-08-17
I recently downloaded Ubuntu and tried it, but fancied the KDE desktop so downloaded and installed KUBuntu on my PC as a dual boot with windows; however I got into confusion with partitioning the hard drive and ideally would like to start again and install Ubuntu first and then, as I understand, install the KDE desktop as a package??....basically can someone tell me how to uninstall Kubuntu (and the boot loader file which lets be choose between XP and Kubuntu) and start again from scratch??

Sorry to be a pain....:confused:

---

### Post by rowanparker on 2006-08-20
Just start the installation again, making sure you choose the previous drive you used and it will overwrite it. Grub will also be reinstalled if you let it.

To install KDE run:
```
sudo apt-get install kubuntu-desktop
```


Rowan.

---

### Post by TheRingmaster on 2006-08-21
it is better to do ```
sudo aptitude install kubuntu-desktop
``` instead because aptitude remembers the things that you would need if you decided to remove kde.

---

### Post by rowanparker on 2006-08-21
Oh right, thanks for that. I just thought apt-get aptitute were the same thing.

---

### Post by TheRingmaster on 2006-08-21
no problem

---

