---
title: "Automatically Disable Touchpad While Typing"
date: 2013-11-04
forum: General Help
---

### Post by cessanfrancisco on 2013-11-04
It appears the "Disable Touchpad While Typing" feature, under "Mouse & Touchpad" settings does not work in Ubuntu 13.10.

Does anyone know of a way to get this feature working, or at least an acceptable work around?

Thanks in advance.

---

### Post by varunendra on 2013-11-05
Open dconf Editor and check **org > gnome > settings-daemon > peripherals > touchpad**. Make sure **disable-while-typing** is enabled there.

If it is already enabled and still has no effect, an 'acceptable' workaround may be to enable **Palm Detection** using **synclient** command and setting its sensitive area value to as low as 2 or 3. Like this -
```
synclient PalmDetect=1
synclient PalmMinWidth=3
```
Although this one would be temporary and you'll need to run the commands at every boot, unless you automate it by adding it to /etc/rc.local or some other way.

---

### Post by cessanfrancisco on 2013-11-06
Thanks.  That seemed to work.

---

### Post by varunendra on 2013-11-06
Great ! Hope it was the fix, not the 'workaround' that worked..

Please mark the thread as [SOLVED] using "Thread Tools" link above the first post. :)

---

