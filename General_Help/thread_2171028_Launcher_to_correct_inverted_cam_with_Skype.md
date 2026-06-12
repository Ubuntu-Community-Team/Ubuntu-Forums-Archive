---
title: "Launcher to correct inverted cam with Skype"
date: 2013-08-28
forum: General Help
---

### Post by alligoodw-live on 2013-08-28
Unfortunately for me, my internal webcam (Asus) is installed upside down. The following script corrects the problem (on my system):

[COLOR=#000000][FONT=Hanuman]exportLIBV4LCONTROL_FLAGS=2 &&LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype 
[/FONT][/COLOR]
What I need to do is create a launcher that will run this command without the use of the terminal. How do I create the launcher (Ubuntu 13.4) to do this? How do I place that launcher on the Unity toolbar?
[COLOR=#000000][FONT=Hanuman]
[/FONT][/COLOR]

---

