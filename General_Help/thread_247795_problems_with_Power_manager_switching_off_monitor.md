---
title: "problems with Power manager switching off monitor"
date: 2006-08-31
forum: General Help
---

### Post by dhruv_1884 on 2006-08-31
Hi guyz,

I had changed the power manager preferences to switch off monitor from the default 30 min to 2 min, but it doesn't switch off after 2 mins, i've noticed that it does switch off after some time though. i reinstalled the sofware and yet no luck,

any suggestions guyz

regards

dhruv

---

### Post by dhruv_1884 on 2006-08-31
any body with a tip!!!!!!

---

### Post by dhruv_1884 on 2006-08-31
:p 
ok guyz figured it out.

as it turns out, gnome-power-manager starts its timer after the idle time required to switch on the screen saver has passed,
for example
if u set your monitor to switch off after 2 mins but if your settings to switch on screensaver were after 13 mins of idle time, then your monitor will switch off after 13 + 2 = 15mins
so if u want your monitor to switch off after 2mins then set the screen saver idel time to 1min and gnome-power-manager time for dispaly to be suspended to 1 min

-

dhruv

---

