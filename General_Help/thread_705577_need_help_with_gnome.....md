---
title: "need help with gnome...."
date: 2008-02-23
forum: General Help
---

### Post by Dracar on 2008-02-23
Ok, I posted this ages ago and it was never fully resolved cause I got pissed and left it go. But I really want to get Ubuntu fixed. I have a dual boot and have like 80% of my hard drive partitioned to Ubuntu, and it doesn't work.

I boot up, it loads everything like it does, then instead of showing the login screen it comes up black and says something about an error. I tried to edit that one file where you set the display driver or what ever, cant remember what its called, but it didn't work, now it shows an error that its configured wrong every time I boot, is there any way I can see if I have Internet, and if so just like reinstall gnome from command line or something, or can some one give me some commands to run to try and fix this?

As of now i get a blue screen with "Failed to start X Server, It is likely it is not set up correctly."

I tried replacing my xorg.conf file with an older one that worked but it gave me some like about not being able to.

---

### Post by nick_h on 2008-02-23
You could try reconfiguring your X server by running:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Dracar on 2008-02-23
Thats the one, I tried that one already. I also tried editing the file manually, but im not sure if i did it right, i went to the x11 folder and ran sudo gedit xorg.conf, but it said it could not open it. I also tried renaming the old one and then renaming a backup but it wouldn't let me do that either, could not rename either one.

---

### Post by Joeb454 on 2008-02-23
Try doing the reconfigure again. And make sure you use the correct options/drivers etc.

Then post back with any errors/output etc :)

---

### Post by Dracar on 2008-02-23
ave done it about 3 times so far today, and about 20 in total, still same results, as for the driver I click vesa cause idk what mine are, and vesa has always worked for me. for those who may know mine, stock dell inspiron b130

---

### Post by Dracar on 2008-02-23
Ive been hacked i just found out, so I really need to switch to ubuntu now, sorry if bumping isn't aloud, but I need a solution to this, my pc is being keylogged right now, can't find it with any scans, so yea....

---

