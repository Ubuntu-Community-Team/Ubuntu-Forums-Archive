---
title: "/usr/lib/pm-utils/power.d doesn't execute automatically the scripts"
date: 2019-10-25
forum: General Help
---

### Post by marsluca7 on 2019-10-25
Hi, i want setup a simple power manager configuration to manage the screen brightness.
To do this i putted this script in this directory "/usr/lib/pm-utils/power.d" and i assigned the correct permission.

> 
#!/bin/bash

case $1 in
    true)
        echo 5625 > /sys/class/backlight/intel_backlight/brightness
    ;;
    false)
        echo 7500 > /sys/class/backlight/intel_backlight/brightness
    ;;
esac


Why when i switch from AC to battery nothing change?
I use Ubuntu 18.04 LTS.

---

### Post by marsluca7 on 2019-10-27
I have also noted that there aren't file connected with pm-utils in */var/log.*
But pm is correctly installed:
> pm-utils is already the newest version (1.4.1-17).


---

### Post by marsluca7 on 2019-10-31
No one can help me?

---

