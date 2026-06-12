---
title: "Can't get webcam to work"
date: 2013-10-12
forum: General Help
---

### Post by bill-lancaster on 2013-10-12
I have a Creative Labs webcam (don't know the model).
Cheese doesn't see it but in Terminal ```
mplayer tv://

``` sometimes will work but mostly it doesn't.
Skype can't see it either.
Audio Settings (Phonon - KDE) has it as UVC Camera (041e:4058.
Any sugestions would be welcome.

Kubuntu 13.04
64bit HP Compaq PC

---

### Post by varunendra on 2013-10-14
Have you tried uvcvideo yet? It's a substitute to cheese with more options.

And please post back the outputs of -
```
usb-devices | grep -B4 -A6 4058
lsmod
```

---

### Post by coldraven on 2013-10-14
Try installing uvcview. Uncheck any "Auto Levels" and adjust the brightness. Then quit, no need to Save, and try Skype

---

### Post by varunendra on 2013-10-14
> **coldraven said:**
> Uncheck any "Auto Levels" and adjust the brightness.

Thanks for pointing that out coldraven. I should remember that.. :)

---

### Post by bill-lancaster on 2013-10-18
Thank you for all the help.  I gave up in the end and purchased a QuickCam Pro 9000.
It worked straight out of the box!

---

### Post by varunendra on 2013-10-18
No problem. Thanks for sharing with us, now we know a model that works out-of-box. :)

---

