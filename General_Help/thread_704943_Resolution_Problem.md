---
title: "Resolution Problem"
date: 2008-02-22
forum: General Help
---

### Post by banditxkr on 2008-02-22
hey everyone i just boght a new usb belkin flip product to use between my windows & ubuntu 7.04 pcs.  the windows installation went just fine (1st time that's ever happened), but ubuntu's screen resolution got screwed up for some reason.  my resolution is stuck @ 640x480 with a refresh rate of 50hz.

a buddy of mine suggested editing the xorg.conf but i had loads of problems with that.  it wouldn't let me save one time, it wouldn't let me edit it another time, i got errors when i tired it in the terminal, and i even couldn't find for a while after that. (very new to ubuntu it's taking me some time to get used of finding everything in the system)

---

### Post by taurus on 2008-02-22
Try reconfiguring your X server from a terminal with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, you can restart your X again so the new settings would be in effect with <Ctrl><Alt>Backspace.

---

### Post by soldats on 2008-02-22
hrmm the code above usually works but that code basically resets it to default which on some machines is 800x640. if you dont enter the -phigh flag you should get a xserver-xorg editor which should let you add some resolutions. just use the spacebar on the resolutions you want then save it and restart X.
i wonder if you werent able to edit xorg.conf becasue you werent using sudo.

also make sure if you do edit the xorg.conf manually you have the refresh rates correctly set otherwise it wont work.

---

### Post by banditxkr on 2008-02-22
thanks guys this fixed my problem instantly

and soldats i was using sudo when it wouldn't let me

---

