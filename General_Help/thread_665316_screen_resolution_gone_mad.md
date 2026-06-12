---
title: "screen resolution gone mad"
date: 2008-01-12
forum: General Help
---

### Post by Ulrik04 on 2008-01-12
I tried to change the driver of my graphics card to make some games working, but then my screen resolution changed to a very small, and even if i change the driver back, i still only can choose max 800x600, where I used to have 1440x900
please help!

---

### Post by overdrank on 2008-01-12
> **Ulrik04 said:**
> I tried to change the driver of my graphics card to make some games working, but then my screen resolution changed to a very small, and even if i change the driver back, i still only can choose max 800x600, where I used to have 1440x900
please help!

HI and have you tried to reconfigure you xorg
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and what is the model of the graphics card?

---

### Post by Ulrik04 on 2008-01-12
itmade my resolution 1280x800, so I can use it now, it's just still very blurry :/ 1440x900 was on the list of availeble resolutions, so i chose that and rebooted, but I came back to 1280x800 again and 1440x900 was gone from the list :/

---

