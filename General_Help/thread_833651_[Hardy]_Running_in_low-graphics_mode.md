---
title: "[Hardy] Running in low-graphics mode?"
date: 2008-06-18
forum: General Help
---

### Post by upshutdown on 2008-06-18
When i logged on today, i got a random error message telling me that im running in low graphics mode. Now my resolution is very low, and i am unable to fix it.
I am relatively new to using this OS so pointing me in a general direction would be greatly appreciated. I am using a Radeon x1950 series.
If more info is needed, let me know.

---

### Post by cdtech on 2008-06-18
Be sure you install the restricted drivers and then check your resolution.

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)

After such you may need to do:
sudo displayconfig-gtk

Hope this helps.....

---

### Post by upshutdown on 2008-06-18
After:
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)

Console returned saying that my drivers are already up to date and installed

Then:
sudo displayconfig-gtk
told me i was using the generic Vesa drivers.
nothing has changed :(

---

### Post by cdtech on 2008-06-18
CTRL+ALT+F1 to tty and login, then
```
sudo pico /etc/X11/xorg.conf
```

Scroll down to the "Device" then "Driver" section. Change from "fglrx" or "ati" or "radeon" to "vesa". Then restart.
```
sudo shutdown -r now
```

If manual editing doesn't work, just reconfigure and select vesa.

---

