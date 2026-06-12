---
title: "kde - how to change boot animation"
date: 2013-01-29
forum: General Help
---

### Post by Jaoyur on 2013-01-29
Hi,

I have this problem: [http://askubuntu.com/questions/248573/kde-how-to-change-boot-animation](http://askubuntu.com/questions/248573/kde-how-to-change-boot-animation)
I did all these steps and nothing worked. I think there is still something that makes problems.
This is my etc/default/grub:[http://paste.ubuntu.com/1587147/](http://paste.ubuntu.com/1587147/)

Right now I don't have now boot animation, there only a black screen with some text.
I have also removed all plymouth-theme-ubuntu-text,plymouth-theme-kubuntu-text etc...
and I have tried all my alternatives and none works:
```
------------------------------------------------------------
  0            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth       100       modalità automatica
* 1            /lib/plymouth/themes/Earth-sunrise/Earth-sunrise.plymouth   50        modalità manuale
  2            /lib/plymouth/themes/fade-in/fade-in.plymouth               10        modalità manuale
  3            /lib/plymouth/themes/glow/glow.plymouth                     10        modalità manuale
  4            /lib/plymouth/themes/solar/solar.plymouth                   10        modalità manuale
  5            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth       100       modalità manuale

```

**edit**: ok I found my problem, it's about my gpu (msi 6870 Hawk) and the proprietary ati drivers: 
I unistalled old 12.8 (even with those the plymouth animation was not working) because I wanted to update my drivers and while I was with open drivers I finally saw the animation on boot, the problem is that I need ati driver and I had to install new 13.1 and infact now plymoth animation doesn't work any more.
So is there a way to solve the problem, now that I found what it is about?
Thanks

---

