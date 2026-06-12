---
title: "help! cpu is 100%!"
date: 2008-05-23
forum: General Help
---

### Post by kopiq on 2008-05-23
hi i just rebooted and my cpu is at full 100% and nothing is running!
i reboted again to see if it was just some screw up but it still is at 100%. everything is soooo slow. the only thing i did last was dl and use was envNG to test my video card. it said there was no support for my ati radeon. now kde is gone full cpu. plz if anyone can help!

---

### Post by Ender305 on 2008-05-23
type ```
top
``` into a terminal and tell us what the processes using the most memory are

---

### Post by kopiq on 2008-05-23
5271 root      20   0  334m  5 84% cpu being used by xorg

---

### Post by kopiq on 2008-05-23
nothing else is using anything big. all under 5 or 2 cpu

---

### Post by kopiq on 2008-05-23
i forgot i also adjust opacity earlyer in the day, but it never took affect, mabey it did now? how do i change it i forget how i got to it in the first place..

---

### Post by drewcoon on 2008-05-23
> **kopiq said:**
> i forgot i also adjust opacity earlyer in the day, but it never took affect, mabey it did now? how do i change it i forget how i got to it in the first place..

Do you have Compiz enabled? It could be eating up all your system resources.

Try System > Preferences > Appearance, then click the "Visual Effects" tab and if it's not set to "none", you could consider disabling it.

---

### Post by ajgreeny on 2008-05-23
Or use terminal (konsole) to stop compiz with ```
metacity --replace
```

---

### Post by kopiq on 2008-05-23
i used envy again, this time choose to install manual. now i rebooted and no graphics card :( envy says my ati readeon is not supported. its a 128 ati radeon 9250/9200.
how can i get the drivers installed?

---

### Post by ajgreeny on 2008-05-24
In versions prior to Hardy Heron you could simply edit the xorg.conf file manually and use the ati (open source, not fglrx) driver for the 9200 card and it should work.  Now the hardy xorg.conf file just says:-

Section "Device"
    Identifier    "Configured Video Device"
EndSection

so I don't know quite how you add the info, or even if it would be read by the graphics system.

In my working Gutsy install the section in xorg.conf says

Section "Device"
    Identifier    "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
    Driver        "ati"
    BusID        "PCI:2:0:0"
EndSection

What would happen if you tried adding that to the hardy xorg.conf, I really don't know but it could be worth trying as long as you back up your current version first so you can get back to it if needed.

---

