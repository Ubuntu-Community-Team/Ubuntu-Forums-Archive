---
title: "HELP!!! Stuck with 640*480 resolution"
date: 2008-07-03
forum: General Help
---

### Post by Calixte on 2008-07-03
Here it is: I installed Ubuntu Hardy and I was stuck with a 800*600 resolution (I have 1600*1240 on Windows XP). Ugly, but usable. After an installation of the nVidia driver (which works perfectly) and a reboot, I am now stuck with a 640*480 res (see attachment).

How can I change the resolution to something livable?

Thanks for your help,
Calixte

PS: I did not have this problem with 7.10

---

### Post by atomkarinca on 2008-07-03
Hit alt+F2 and type "displayconfig-gtk" (without the quotes), configure your monitor and select a decent resolution. Then open up Nvidia Settings with root privilages:

```
gksudo nvidia-settings
```

hit "Save to X Configuration File" button and that should be it.

---

### Post by Calixte on 2008-07-03
OK, worked
Thanks :)

---

### Post by atomkarinca on 2008-07-03
Not a problem :)

---

