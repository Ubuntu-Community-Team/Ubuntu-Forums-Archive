---
title: "System sound is small"
date: 2008-03-20
forum: General Help
---

### Post by SuperBo on 2008-03-20
My sound volume is very small. How can i fix this. I have change volume to 100 % in volume manager.

---

### Post by notwen on 2008-03-20
Have a look at alsamixer, open a terminal and enter the following command, adjust as necessary:

```
alsamixer
```

Sometimes after installing Ubuntu, certain channels are turned all the way down by default, in turn very low sound if any.  After you get your desired volume, hit ESC to exit alsamixer and close your term.  You may wish to reboot also to ensure the settings were saved.

---

### Post by SuperBo on 2008-03-22
Thank you, I fixed sound error.
In device for Mixer track, what I should choose? (Master or Pc Speaker)

---

### Post by danwood76 on 2008-03-22
Normally you use Master and have the PC speakers or whatever turned all the way up.
If you use master then when you plug in headphones you still get volume control.

---

### Post by SuperBo on 2008-03-23
How can reset sound config. Before, my sound volume is not small.

---

