---
title: "Disable 'Sleep and Charge' in Toshiba Laptops"
date: 2013-08-27
forum: General Help
---

### Post by vdeepakkumar on 2013-08-27
Dear KDE Team,

I am currently using a Toshiba Satellite C655 laptop. As people might be aware, Toshiba has a feature like even when the laptop is turned off, the USB is empowered to charge other devices thus discharging its battery. For Windows, Toshiba gives a tool, I believe to disable this 'sleep and charge' feature.

Can some one help guide how to disable this feature in Ubuntu?

---

### Post by tgalati4 on 2013-08-28
Install *acpitool*.  Display the USB ports with it, then disable the ports that you want to sleep without power.

```
sudo apt-get install acpitool
man acpitool
acpitool -w 
```

---

