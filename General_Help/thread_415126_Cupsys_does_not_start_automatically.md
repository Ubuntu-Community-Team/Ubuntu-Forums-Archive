---
title: "Cupsys does not start automatically"
date: 2007-04-20
forum: General Help
---

### Post by Zeroangel on 2007-04-20
Hi all, Kubuntu user here.

Anyways, I'm having a little bit of a problem. My printer doesnt work unless I start cupsys manually. I can work around it by creating a desktop shortcut with this command
```
kdesu /etc/init.d/cupsys restart
```While its not a huge problem, it does confuse the windows users in the house as to why they have to click on a desktop shortcut to get printing working properly. 

I would like to know how to start cupsys automatically.

Also, the print kio slave allows me to select different printing systems. Is CUPS the best for my printer or should I use another one? FYI my printer is a EPSON STYLUS CX1500.

Thanks in advance,
Zero Angel

---

### Post by Zeroangel on 2007-04-21
*bump!*

---

### Post by mhansen on 2007-04-21
Do you have a cupsys startup script in /etc/rc2.d?

---

### Post by Zeroangel on 2007-04-22
Nope, but there are cups related files in the following locations

/etc/rc0.d/K19cupsys
/etc/rc1.d/K19cupsys
/etc/rc3.d/S19cupsys
/etc/rc4.d/S19cupsys
/etc/rc5.d/S19cupsys
/etc/rc6.d/K19cupsys

Aha! I think I have an idea....

EDIT: Thanks! :KS
I linked /etc/rc2.d/S19cupsys to /etc/init.c/cupsys and now it starts automatically. :D

---

