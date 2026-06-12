---
title: "graphics driver install ruind x how do i fix it?"
date: 2007-05-11
forum: General Help
---

### Post by hessiess on 2007-05-11
tryed to install a driver for my nvidia graphics card, now i have no desktop, only a command line. 

how do i fix it? carnt go back to old setup becose it ses no file found, or somthing like that.

tryed
sudo dpkg -reconfigure -phigh xserver-xorg
witch dident do anything.

copying anything to the form will be a problem.

---

### Post by Ateo on 2007-05-11
When your GUI tries to load (GDM/KDM), it should kick you back to an 'X error' screen. Usually ugly in appearance. This is Xorg crapping out and it should also ask you if you want to see the log. Read the log.

If this doesn't happen, read /var/log/Xorg.0.log to get some clues. But I suspect we'll need to peak at your xorg file somehow.

---

### Post by hessiess on 2007-05-11
if somone can tell me how to get it onto the windows partition using a comand line then il post it, i dont even know were its locaed. i need the graphics driver becose blender will only run 1000 polys without it. im trying to ditch windows, so i never haft to use vista.

i could wirght down the error output and post that, but becose im deslexic this will take ages and is verry likly to have some errors.

im using fisty. becose im new to linux i havent got a clue whats going on, i expected the driver to install perfectualy.

---

### Post by Ateo on 2007-05-11
Well, YOU have to do something for us to help you. We can't read nor guess what's at your end.

Do your best. We'll try to help.

From the command line prompt, just log in with your regular user. Then, type```
$ cat /var/log/Xorg.0.log | less
```

This will dump your xorg log to your screen, one page at a time. Hit the space bar to continue.

---

### Post by carolinason on 2007-05-11
If you really don't care about windows,  and your linux install has nothing important, the easiest thing for you to do is reinstall feisty and allow it to use the entire drive.

Use automatix to try and install your card.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by hessiess on 2007-05-11
i carnt do without windows at the moment becose i need some windows only programs for my schoolwork. and i only have working internt on windows.

> 
Well, YOU have to do something for us to help you. We can't read nor guess what's at your end.

Do your best. We'll try to help.

From the command line prompt, just log in with your regular user. Then, type
Code:

$ cat /var/log/Xorg.0.log | less

This will dump your xorg log to your screen, one page at a time. Hit the space bar to continue.

do you want me to copy it to the form? how long is it?

---

### Post by hessiess on 2007-05-11
ive photograohed the output of the error mesage, but i carnt post the images on the form becose thay are to big, and carnt srrink them becose it makes the text unredable.
i will email them to anyone who can healp me, there 5mp images. it would take howers for me to type it all out.

abit at the end ses loading modual nvidia, could not load modual, unloading modual nvidia.

tryed "$ cat /var/log/Xorg.0.log | less" but it gust went on to the next line without doing anything

---

### Post by hessiess on 2007-05-11
bump

---

### Post by hessiess on 2007-05-11
bump

---

### Post by hessiess on 2007-05-12
bump

---

### Post by hessiess on 2007-05-12
ive got it working agen, but not with the proper card driver. blender will onlt run 3000 polys without the driver, my modals are usaly 100k+polys. in windows it maxis at 150k polys

---

### Post by hessiess on 2007-05-12
bump

---

