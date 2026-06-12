---
title: "black screen after initial installation"
date: 2007-08-15
forum: General Help
---

### Post by jc364 on 2007-08-15
I have just installed Ubuntu using Wubi, and I have an issue with startup.  I have installed Ubuntu on other systems, but on my own I get a black screen before the login screen appears.  The monitor is still receiving signal, but the screen is completely black.  I am assuming it is some sort of driver issue; my graphics card is a NVidia GeForce 6800XT.  I am still pretty new to Ubuntu, so I was wondering if anyone has any troubleshooting suggestions.  Thanks!

---

### Post by ago on 2007-08-16
You'll need to install the drivers. Search this forum as this has been dealt with in the past

---

### Post by jc364 on 2007-08-24
I am finally up and going.  Here are the commands that I had to enter to get Ubuntu going with a GeForce 6800XT:
```
sudo apt-get update
sudo apt-get install nvidia-glx
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

These commands had to be entered in recovery mode, since a command line could not be reached in a normal startup.

---

