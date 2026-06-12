---
title: "no menu bar in beryl"
date: 2007-04-08
forum: General Help
---

### Post by Donhu on 2007-04-08
after running beryl, my menu bars disappear, what could've happened and how can i fix it?

---

### Post by bashologist on 2007-04-08
Menu bar? Can you be more specific? Can you paste your xorg.conf file please? [http://www.rafb.net/paste/](http://www.rafb.net/paste/)

---

### Post by Donhu on 2007-04-08
URL: [http://rafb.net/p/gp46tG60.html](http://rafb.net/p/gp46tG60.html) 

after running beryl, i cannot minimize windows, or close

---

### Post by bashologist on 2007-04-08
> **Donhu said:**
> URL: [http://rafb.net/p/gp46tG60.html](http://rafb.net/p/gp46tG60.html) 

after running beryl, i cannot minimize windows, or close

I'm not sure what to do but if I had to guess I would suggest adding the following under your device section:
```
Option         "AddARGBGLXVisuals" "True"
```
So in other words your xorg.conf should look like this:
```
Section "Device"
        Identifier      "Intel Corporation 945G Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "AddARGBGLXVisuals" "True"
EndSection
```
You can add it manually with this command:
```
sudo nano /etc/X11/xorg.conf
```
If your right alt button doesn't work then removing this line should fix it.
```
Option          "XkbOptions"    "lv3:ralt_switch"
```

---

### Post by Donhu on 2007-04-08
i made the changes but i still do not have any of my menu bars...do you think it is a problem with the actual settings of beryl?

---

### Post by bashologist on 2007-04-08
> **Donhu said:**
> i made the changes but i still do not have any of my menu bars...do you think it is a problem with the actual settings of beryl?

Did you restart your display manager with alt+ctrl+backspace or reboot? If it's still not working after a reboot then maybe try executing beryl-manager from a terminal and pasting the error message. Maybe forcing aiglx might help.

---

### Post by Donhu on 2007-04-08
after running the comman beryl in the terminal, it runs but there's an error message in the terminal saying, 
libGL warning: 3D driver claims to not support visual 0x5b
Reloading options...
i dont have beryl on auto boot so when i restart, i have to re-run it

---

