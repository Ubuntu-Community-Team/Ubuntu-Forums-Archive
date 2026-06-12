---
title: "[SOLVED] Increase screen resolution"
date: 2007-09-14
forum: General Help
---

### Post by mikecomua on 2007-09-14
Hi, I have a Dell Inspiron e1405 with a beautiful 14.1 1440x900 pixels resolution. I  love Ubuntu, but I would like to increase my resolution to at least 1280 x1024. Strange  thing is when I boot into puppy my resolution is 1440x900. I can't reconfigure my xorg.conf file because I have no idea which parameters my screen has. Can I copy my xorg.conf file from puppy and paste it into my Ubuntu? THX

---

### Post by jamvegan on 2007-09-14
I've had issues with copying xorg.conf files from one OS to another.  Have you tried just changing the Modes lines in the Screen section of xorg.conf to mirror your puppy configuration?

---

### Post by fragos on 2007-09-15
First, 900 may be your maximun vertical resolution.  To maintain the same aspect ratio, 1280x800 would be correct.  Your image will be distorted if you don't keep the same aspect ratio.

---

### Post by mikecomua on 2007-09-15
I just visited Dell's forum and found a driver

---

