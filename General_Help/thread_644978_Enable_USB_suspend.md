---
title: "Enable USB suspend"
date: 2007-12-19
forum: General Help
---

### Post by apoth on 2007-12-19
Powertop is trying to encourage me to enable USB suspend, which I'd be happy to do and it seems to be able to do when I press U - but does anyone know how I can make that change permanent so it will survive a reboot?

Thanks

---

### Post by cyberdork33 on 2007-12-19
> Suggestion: Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub configI think it tells you.

Add "usbcore.autosuspend=1" to the end of your kernel line(s) in the /boot/grub/menu.lst file

---

### Post by apoth on 2007-12-20
It did suggest that, but it didn't work - some error about the option not existing and being ignored?

---

### Post by camel1cz on 2008-01-27
Hi, on my system I found several autosuspend files in the /sys directory tree (under usb)... they seem to have default value of 2 and powertop changes it to 1... so some simple scripting can do the trick:

```

#!/bin/bash

for i in `find /sys -name autosuspend -exec echo {} \;` ; do echo "1" > $i ; done

```

I'm not sure it it's all (cause powertop still offers to turn it on) but in seems to have positive impact anyhow...

---

