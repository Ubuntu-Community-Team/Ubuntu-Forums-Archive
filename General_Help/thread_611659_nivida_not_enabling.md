---
title: "nivida not enabling"
date: 2007-11-13
forum: General Help
---

### Post by onlyproductions on 2007-11-13
hi, i got ubuntu to wrk on my friends comp, i click on desktop effects and it says u need to enable nivida driver then it has two buttons cancel and enable driver.i click the latter and it says please run desktop effects after restarting the computer with the new graphics driver active. so i restart, click on the desktop effects and the same thing happens, how do i "activate the driver"

---

### Post by PmDematagoda on 2007-11-13
Try this in Recovery Mode or by killing the X-server:-

```
sudo dpkg-reconfigure xserver-xorg
```

select the driver as Nvidia, select any other options you need. After reconfiguration do:-
```

sudo startx
```

Then see if your problem is solved.

---

