---
title: "hdajackretask throws error"
date: 2018-05-24
forum: General Help
---

### Post by klundermann on 2018-05-24
In the past, I have been able to [use  hdajackretask  to get the subwoofer working](https://ubuntuforums.org/showthread.php?t=2386765&highlight=hdajackreset) on an ASUS laptop.  Under either 17.10 or 18.04, however, I get an error when I click "Apply now".

**tee: /sys/class/sound/hwC1D0/reconfig: Device or resource busy**

Would anyone know what I can do about this?

---

### Post by klundermann on 2018-06-08
I found a work-around on another forum: skip the testing phase (clicking "Apply now") and just write your changes to disk (click "Install boot override") and reboot.

Obviously this would be clumsy if you were proceeding by trial and error, but in my case the fix worked the first time.

---

