---
title: "Different screen Res on dual screen"
date: 2007-04-30
forum: General Help
---

### Post by lynxus on 2007-04-30
Hi guys,
I have a IBM R51 laptop running the default ATI drivers.

In fedora core i used to be able to plug an external monitor in and have that running on 1024x768 res while my laptop screen stayed at 1400x???? whatever the res is.

Both screens had separate desktops also. So one was a clean desktop at 1024 while the other was my normal desktop on 1400.



How can i do this is Ubuntu? It doesn't come with the normal DISPLAY app in system that fedoa came with. The only display options i have is change my screen res.


Any ideas? anyone?

Cheers
G

---

### Post by lynxus on 2007-04-30
Bump ?

---

### Post by borobudur on 2007-05-01
You have to edit the /etc/X11/xorg.conf file.

This is a part out of that file:
```
Section "ServerLayout"
        Identifier      "Xinerama"
        Screen          0 "Default Screen[0]" 0 0
        Screen          1 "Default Screen[1]" LeftOf "Default Screen[0]"
        ...

```But there is more to do. You can follow this:
[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

---

