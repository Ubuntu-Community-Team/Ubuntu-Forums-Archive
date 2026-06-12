---
title: "Filezilla User Input Problems"
date: 2015-06-01
forum: General Help
---

### Post by jonathan81 on 2015-06-01
In Filezilla, if I am typing and try to use a back space or the arrow keys, nothing happens. But if I am typing normally then the input works fine. This is very frustrating for me as I make a lot of typing errors.

All other programs seem to work fine.

How could I debug/fix his?

---

### Post by Dennis N on 2015-06-01
In a few applications, there can be text or data entry problems due to ibus being enabled. Chromium was one of these, but I'm not sure on Filezilla. I don't have it installed.

You could try disabling ibus -  I have disabled ibus in both Lubuntu 14.04 and 15.04:
Preferences > Language Support > (close any pop up window) > Keyboard Input Method System > change from ibus to none.
Might need to log out and log back in to see any change.

---

### Post by jonathan81 on 2015-06-01
Thanks Dennis. That worked!

---

### Post by ghmercado on 2015-08-11
reactivated my long dormant ubuntu forum account just to say THANK YOU. This solution worked. Ibus needs to be looked at.

---

### Post by Alb673 on 2015-08-16
Thanks Dennis had same issue and your solution worked a treat :)

---

