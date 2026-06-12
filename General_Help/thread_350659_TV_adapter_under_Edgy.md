---
title: "TV adapter under Edgy"
date: 2007-01-31
forum: General Help
---

### Post by Pizza the Hutt on 2007-01-31
I have an ATI TV adapter and want to install it under Edgy to watch TV. Where can I get the drivers and software and how do I install them?

---

### Post by reclusivemonkey on 2007-02-01
> **Pizza the Hutt said:**
> I have an ATI TV adapter and want to install it under Edgy to watch TV. Where can I get the drivers and software and how do I install them?

Model number? Not all ATI TV cards are supported. If it is supported, the drivers are most likely installed already. TVTime is a great TV viewer, easy to use and configure. Just install with your preferred package manager.

---

### Post by Naegling23 on 2007-02-01
I use an ati tvwoner pro.  I didnt need to install any drivers, just download tvtime and try to get it configured.

---

### Post by Pizza the Hutt on 2007-02-02
I have installed TV Time, but nothing happens when I click on the icon.

---

### Post by Vox754 on 2007-02-02
I have a TV Card, saa7134 chipset, that doesn't work with TvTime, so instead I use "xawtv".
It doesn't have a pretty interface but if you don't care you may watch TV on it, provided that the driver works and your tuner is set correctly.

You may need to manually edit a configuration file for the driver, in my case it is "/etc/modprobe.d/saa7134".

Once you have installed "xawtv" it is best to create a configuration file for it.
```
scantv -o ~/.xawtv
```

---

### Post by Pizza the Hutt on 2007-02-24
I got it to work with TVtime. Thanks for help.

---

