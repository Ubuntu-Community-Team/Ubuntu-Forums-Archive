---
title: "xserver problems"
date: 2007-04-12
forum: General Help
---

### Post by tpdasf on 2007-04-12
I'm running edgy and using a GeForce4 MX 440 graphics card.
In an attempt to fix what seemed like a driver issue, I followed a few tutorials on how to install the nvidia drivers (I think one of them was called something like edgy guide to installing nvidia drivers). I also installed a script called 'envy'. After running the envy one, everything seemed slow to show up. Right clicking on the desktop would cause the menu to *slowly* show. So I decided on using the other guide. After this, when trying to restart the xserver I got a message that it couldn't start.
I tried dpkg-reconfigure xserver-org and that didn't work. I also tried using a backed up xorg.conf file which didn't work either. I think it's a problem with something being installed or installed which shouldn't be.

Does anyone know anything I can try?

EDIT: I was using this guide (method 1) [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by tpdasf on 2007-04-13
Anyone? I've tried searching for an answer but nothing seems to work.

---

### Post by zvacet on 2007-04-13
```
sudo dpkg-reconfigure xserver-xorg
```

replace **nvidia** with **nv**

---

### Post by tpdasf on 2007-04-13
I tried that, same thing. Also tried "vesa" I think it was, didn't work

---

### Post by tpdasf on 2007-04-13
bump

---

### Post by tpdasf on 2007-04-14
Anyone?

---

