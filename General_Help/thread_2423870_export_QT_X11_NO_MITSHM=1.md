---
title: "export QT_X11_NO_MITSHM=1"
date: 2019-07-30
forum: General Help
---

### Post by hazard-droid on 2019-07-30
Hi, I just installed Ampps on my ubuntu 18.04x32 (Upgraded from ubuntu 16.04 x32bit) but as I run the app the GUI was broken as I saw a gray window I search a bit and found the solution but not permanent Environment variable **QT_X11_NO_MITSHM** was not set. 

Runtime solutions: 
sudo **QT_X11_NO_MITSHM=1** /usr/local/ampps/Ampps


which works but I have to do this everytime instead of just doing sudo ./Ampps The Permanent Solution:  is to Add **export QT_X11_NO_MITSHM=1** to **/etc/environment** or to your environment file based on your Linux distro but idk how to do that so can anyone guide me how to do that?

---

### Post by dragonfly41 on 2019-07-30
I would add that line in ~/.profile

---

