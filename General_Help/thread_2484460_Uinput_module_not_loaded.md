---
title: "Uinput module not loaded"
date: 2023-02-27
forum: General Help
---

### Post by francbe83 on 2023-02-27
Hello everyone,

i'm facing a problem i've been unable to solve despite having been searching the web for numerous days :/

i'm trying to use a PS4 controller to play games in Yuzu (the controller itself is recognized and usable right after being plugged in), to enable motion detection i installed DS4DRV using this procesure : [https://github.com/epigramx/ds4drv-cemuhook](https://github.com/epigramx/ds4drv-cemuhook)

The problem is that the uinput module isn't loaded (/dev/ contains a empty uinput file), i cannot find any uinput.ko file anywhere neither.

I've read quite a few times that the issue might be caused by permissions to write the uinput file, in my case the command "sudo modprobe uinput" returns no error.

Has anyone encountered this kind of problem before ?

Thanks in advance.

---

