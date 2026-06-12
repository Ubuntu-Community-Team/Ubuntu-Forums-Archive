---
title: "Ubuntu won't start after failed sound driver install"
date: 2008-05-17
forum: General Help
---

### Post by Cubibubi on 2008-05-17
Hello,

yesterday I finally tried to install some drivers for my sound card, the Creative Soundblaster X-Fi. Although I hadn't had everything configured right and didn't have all packages I needed and didn't have all configured kernels and ALSAs (I'm new to Linux), I typed ./configure and sudo make. That worked somehow. 
Without expecting the next command to work, I typed sudo make install. (Well I knew and now i know even more that that was very stupid, please don't tell me that.)

Then Ubuntu gradually freezed and I had to hardcore restart my PC (with the LED button = actually by turning off the power).

From then, everytime i start Ubuntu it loads until it has to load the sounddrivers. I tried rescue mode, and it convinced me that it stops at the sounddrivers.


Now my question is: How can I disable/deinstall/turn-off-when-starting-up my sound drivers via command line (in the rescue mode)?


Thank you VERY MUCH in advance!


EDIT: Now that I installed a piece of software letting me access my Linux harddrive from Windows, I can also manually delete certain driver files, so this kind of help would be appreciated as well!

---

### Post by strabes on 2008-05-17
I do not know the name of the kernel module for the (awful) linux drivers for the x-fi series of soundcards. However, if you do find it out, you can boot into recovery mode, blacklist it, and then try starting ubuntu normally. To do this you must first find the name of the kernel module for these drivers. Then run this command in recovery mode:```
sudo nano /etc/modprobe.d/blacklist
```Add the following line to the end of that file:> blacklist kernelmodulename
Save the file by hitting Ctrl+O and exit by hitting Ctrl+X. Reboot by running sudo reboot and the problem may or may not be fixed.

---

### Post by Cubibubi on 2008-05-18
Hello! Thank you VERY much, I'll try it out. By the way, I can edit the file from Windows, so it's at least that bit easier :)

---

### Post by Cubibubi on 2008-05-18
but strabes, do you know how perhaps the driver might be called? or where i can find that?

---

