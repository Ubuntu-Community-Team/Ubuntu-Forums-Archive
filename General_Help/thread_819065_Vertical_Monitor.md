---
title: "Vertical Monitor"
date: 2008-06-05
forum: General Help
---

### Post by ductiletoaster on 2008-06-05
Hello so i wanted to know how i can set up vertical Monitor or instead of display lets say 800X600 i could display 600X800.....? 

I have a Nvidia Geforce 6800gs and im running Ubuntu 8.04!

O and i tried just goin into prefrences/screen resoluition
and that only gives me the normal option to rotation!

thanks in advance!

---

### Post by Forlong on 2008-06-05
Running ```
xrandr -o left
``` in the terminal  should do the trick.

And/or add
```
Option "RandRRotation" "1"
``` to the **Section "Device"** of your **/etc/X11/xorg.conf**

---

### Post by ductiletoaster on 2008-06-07
Sorry this took so long..... ok so i tried xrandr -o left
and this is what i got 

```

  X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  158 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

---

### Post by ductiletoaster on 2008-06-07
Ok so i tried your second option and that worked...... kinda! so i know have the option to rotate it but it will rotate it and then go back to its original settings! my guess is because the resolution it set for 1280 X 1024 when it needs to be 1024 x 1280! how can i add this option in xorg.conf or is there something im missing

---

### Post by ductiletoaster on 2008-06-07
Awww never mind lol i got it i tired it agian and the setting set! however i have another question now how can i change the refresh rate mine only allows to 51 but i know my mmonitor can take up to 75!

---

### Post by Forlong on 2008-06-08
Add this to the **Section "Monitor"**```

	VertRefresh	55-75
```
(the first value can vary, of course -- have a look at your monitor's manual)

---

