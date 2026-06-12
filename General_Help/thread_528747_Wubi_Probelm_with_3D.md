---
title: "Wubi Probelm with 3D"
date: 2007-08-18
forum: General Help
---

### Post by charliedog on 2007-08-18
I installed wubi and all went well, installed all the updates again all well.
Went and changed the system to 3D it then downloaded the driver , prompted to reboot and now it wont load, it says something like failure to start xorg server , im presuming changing to the 3D driver has screwed something up, how to I change back again
thanks

---

### Post by w4ett on 2007-08-20
From the terminal type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

select 'vesa' as your video river and save, and from the terminal:
```
startx
```

---

### Post by charliedog on 2007-08-20
thanks I will give that a whirl and report back 

thank you for the reply :)

---

