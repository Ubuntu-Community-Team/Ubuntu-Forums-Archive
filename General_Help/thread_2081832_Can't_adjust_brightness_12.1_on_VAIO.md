---
title: "Can't adjust brightness 12.1 on VAIO"
date: 2012-11-07
forum: General Help
---

### Post by cottoz on 2012-11-07
I'm unable to adjust the brightness from the function keys and from the system settings on my VAIO SVT13114 (Ultrabook).  I've tried the adjustment to GRUB with the "quiet splash" and the "vendor" setting, but it didn't have an effect.  I'm still at full brightness.  Thank you for any help you can give me.

--
cottoz

---

### Post by cottoz on 2012-11-08
Some more information:

This allows me to adjust the brightness from a terminal window...

```
echo 1200 | sudo tee /sys/class/backlight/intel_backlight/brightness > /dev/null
```But, I still can't adjust by function keys or in system settings.

---

