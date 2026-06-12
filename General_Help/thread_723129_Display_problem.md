---
title: "Display problem"
date: 2008-03-13
forum: General Help
---

### Post by dayanandasaraswati on 2008-03-13
Hi, 
     Yesterday i installed ubuntu and downloaded a video driver. That driver prompted me to restart display and when done so, my display got scrambled and a message says "ubuntu is working in low graphics mode". During the installation of the driver my xorg.conf was not backed up, so i'm unable to get back my normal display. I also tried reconfiguring xserver  but nothing proved fruitfull. Please help me with a solution

---

### Post by taurus on 2008-03-13
You mean you ran this command from a terminal and it didn't help?

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
What kind of graphic card do you have anyway?

---

### Post by dayanandasaraswati on 2008-03-13
Ya i ran the command > sudo dpkg-reconfigure xserver-xorg
  I already have ubuntu 7.10 installed in my system. I downloaded Ubuntu Ultimate dvd and installed it. This ultimate edition created the problem as it had downloaded video drivers without my knowledge. I am telling all these because in my normal ubuntu 7.10 display is working on cool. 
I have ATI Radeon Xpress 200 on board graphics card which comes with intel 102GGC motherboard

---

