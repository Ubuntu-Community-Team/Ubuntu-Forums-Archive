---
title: "Installing Gutsy (ubuntu 7.10) on a Dell Inspiron 531s"
date: 2007-12-21
forum: General Help
---

### Post by messadua on 2007-12-21
Dear Ubuntuers, 

I am thinking to buy a Dell Inspiron 531s to install Ubuntu 7.10. 
Checking the hardware, I have two options regarding the video card : 

1) NVidia GEforce SE Integrated graphics 

2) ATI Radeon HD 2400 Pro 

Looking around (this forum and elsewhere) I noticed that more  that some users had problems installing the NVdia. Anyone here can confirm this feeling: is that NVidia card integrated onboard difficult to make work with Gutsy ? 
In that case: 

1) Do you have some advices on how to workaround (Links, tutorials or whatever) 

2) I better would choose the ATI (a little bit more expensive) card to avoid future problems ? 

Thank you !

Diego

---

### Post by Pumalite on 2007-12-21
Both graphics are a problem. Install with the Alternate CD and configure your xserver at the end of the installation. 
[http://ubuntuforums.org/showthread.php?p=3966650](http://ubuntuforums.org/showthread.php?p=3966650)

---

### Post by messadua on 2007-12-21
Thank you for the quick reply, 

In effects I had read that review, and it looks like he did not have to use the alternate CD. 
I would install the server version and thereafter the desktop one (just to have a GUI, but I need the server capabilities). 
Do you think the Restricted server through Synaptics could work ? 
In alernative, do you have some links on how set up the NVidia by the textual terminal ? 

Diego

---

### Post by Pumalite on 2007-12-21
Nvidia:
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
sudo sh /path/to/the/driver/NVIDIAxxxx.run
sudo /etc/init.d/gdm start
Make sure you have first:
sudo apt-get install build-essential

---

### Post by messadua on 2007-12-21
Great ! Thank you very much, so is there no way to make it work with the restricted server drivers ?

---

### Post by Pumalite on 2007-12-21
You are welcome. That's the way I use. I don't know about restricted 'server' drivers. Good luck!

---

