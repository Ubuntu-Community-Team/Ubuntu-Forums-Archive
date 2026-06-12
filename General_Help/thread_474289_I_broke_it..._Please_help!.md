---
title: "I broke it... Please help!"
date: 2007-06-14
forum: General Help
---

### Post by Phayder92889 on 2007-06-14
I boot up, XServer crashes. I restore xorg.conf to a previous state, start GDM, beryl crashes. I reinstall the linux driver that I've removed all reference to, reboot, XServer crashes again.

Um... I manually edited xorg.conf in an attempt to activate/use my second monitor, and I think that's what did it. I rebooted about a dozen times after installing the driver, and it was fine. I accept that I'm an idiot, and that I probably shouldn't dick around with things outside my comprehension. Keeping all that in mind, please help?

---

### Post by Crafty Kisses on 2007-06-14
> **Phayder92889 said:**
> I boot up, XServer crashes. I restore xorg.conf to a previous state, start GDM, beryl crashes. I reinstall the linux driver that I've removed all reference to, reboot, XServer crashes again.

Um... I manually edited xorg.conf in an attempt to activate/use my second monitor, and I think that's what did it. I rebooted about a dozen times after installing the driver, and it was fine. I accept that I'm an idiot, and that I probably shouldn't dick around with things outside my comprehension. Keeping all that in mind, please help?

This should solve the issue, try this:
```
sudo dpkg-reconfigure xserver-xorg
```

---

