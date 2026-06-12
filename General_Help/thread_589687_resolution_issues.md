---
title: "resolution issues"
date: 2007-10-24
forum: General Help
---

### Post by yon2501 on 2007-10-24
ok so i just dual booted gusty on my laptop with windows at the other OS (basically for a game-box) but for some reason whenever i log off of ubuntu it resets the resolution to 840 X 545 the res i normally use is 1400 X 900 and i have to manually go into system > administration > screens and graphics and change it back to normal. i have an Nvidia Quadro 1500 graphics card and im using the nvidia-glx-new graphics driver. anyone have any idea what my problem might be?

---

### Post by Qwerty_ on 2007-10-24
Reconfiguring your xserver might fix this problem for you.

```
sudo dpkg-reconfigure xserver-org
```

---

### Post by yon2501 on 2007-10-24
um it didnt work inface i got an error saying that xserver-org isnt installed

---

### Post by por100pre1 on 2007-10-24
> **yon2501 said:**
> um it didnt work inface i got an error saying that xserver-org isnt installed

```
sudo aptitude install ubuntu-desktop
```

That should install any missing packages, let us know if this works. :-k

---

### Post by yon2501 on 2007-10-24
still says the same thing :/

---

### Post by por100pre1 on 2007-10-24
That's no good. Try this then:

```
sudo aptitude reinstall xserver-xorg
```

Your system seems to be in a really bad condition...

---

### Post by yon2501 on 2007-10-24
that didnt work but ive been tweeking and ive got it working for everything but the login screen but oh well it works is what matters

---

