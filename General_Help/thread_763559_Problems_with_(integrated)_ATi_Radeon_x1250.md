---
title: "Problems with (integrated) ATi Radeon x1250"
date: 2008-04-23
forum: General Help
---

### Post by Canis familiaris on 2008-04-23
I have Ubuntu loaded on as ASUS M2A-VM motherboard with integrated ATi Radeon x1250 graphics.
I followed the instructions on enabling binary drivers from ATI site:
_[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)_
using Catalyst way (fglrx drivers do not work), but after I rebooted, the monitor turned off and I could only end up using Crtl + Alt + F1 to bring CUI and had to reconfigure xserver to dpkg. 

I want to use ATi drivers for Compiz. Please help.

---

### Post by Ub1476 on 2008-04-23
First, remove the manually installed Catalyst driver. Next, download [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") which can install and configure the the latest fglrx driver for you. There's an option to remove previously installed drivers there too (but I suggest you double-check here). Envy can be run in graphical or text mode:

```
envy -g

envy -t
```

If it asks you to configure X, say yes.

---

### Post by Canis familiaris on 2008-04-23
Thanks UB1476

It works like a treat

---

