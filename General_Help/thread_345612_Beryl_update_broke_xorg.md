---
title: "Beryl update broke xorg"
date: 2007-01-24
forum: General Help
---

### Post by cmmike1 on 2007-01-24
Recently i decided to update to the new version to .2 and i got a white screen. i figured i would just restart X but when i did it came up with a xorg error saying that it couldn't find any screens. I tried to restore my xorg because i had one saved in my home folder for when i installed twinview but it didn't restore. This is what i typed into the terminal in restore mode.
> sudo cp /home/mike/xorg.conf /etc/X111/xorg.confI'm thinking that maybe  I'm typing in the wrong location for my home folder but i would want someone to confirm it. I would like to restore it so I can start using Ubuntu again and reinstall beryl.

---

### Post by energiya on 2007-01-24
> **cmmike1 said:**
> sudo cp /home/mike/xorg.conf /etc/X111/xorg.conf

Shouldn't it be /etc/X11/xorg.conf ?

---

### Post by ~LoKe on 2007-01-24
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by cmmike1 on 2007-01-24
> **energiya said:**
> Shouldn't it be /etc/X11/xorg.conf ?

yes that is what i meant to say.

and to the person above this i want to restore if at all possible and not reconfigure. i suppose i could reconfigure it then restore. i will have to give this a try.

---

