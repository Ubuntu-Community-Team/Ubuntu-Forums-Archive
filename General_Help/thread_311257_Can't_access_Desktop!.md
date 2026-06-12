---
title: "Can't access Desktop!"
date: 2006-12-02
forum: General Help
---

### Post by Kittie Rose on 2006-12-02
I adjusted the monitor refresh rate; my computer then gave me a black screen with a flashing underscore. I eventually got landed in the X Window system which told me it couldn't find my output!

I just get dumped into the console whenever I boot now. Windows is working fine(Ironically).

Please help me, I have to get some assignments done for college by monday, they have to be done in Linux...

---

### Post by Kittie Rose on 2006-12-02
This is really urgent! I can't access anything useful without GNOME... what do I do!? Why isn't it picking up my display? Even "safe mode" doesn't work...??? How do I reset my display settings?

---

### Post by taurus on 2006-12-02
Boot into recovery mode from GRUB menu and change /etc/X11/xorg.conf back to whatever it was before you decided to make changes to it!!!

```
nano -w /etc/X11/xorg.conf
```

---

