---
title: "Hardy Heron, nVidia and Desktop Effects"
date: 2008-05-03
forum: General Help
---

### Post by Lelouch on 2008-05-03
I have nVidia GeForce 7400. In hardy heron, the 'restricted' driver for my nVidia card is enabled but the 'In use' icon is red...

I tried to enable the desktop effects, but got 'Couldnt enable desktop effects' error

Should i install an additional driver?

---

### Post by Zorael on 2008-05-03
Try entering this in a terminal.
```
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```
Then restart X with Ctrl+Alt+Backspace. Save your work first.

---

### Post by Lelouch on 2008-05-03
nvidia-xconfig command not found

---

### Post by Zorael on 2008-05-03
Then you don't have the Nvidia drivers installed. :>

```
$ sudo aptitude install nvidia-glx-new nvidia-settings
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```

---

