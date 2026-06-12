---
title: "Auto Brightness depending on power source"
date: 2013-01-13
forum: General Help
---

### Post by BRKsays on 2013-01-13
Is there any way to make Ubuntu remember different brightness settings when I'm plugged in and when I' plugged out like windows? I dim the brightness to the minimum when I'm running my laptop on battery as my laptop gives at best three hours of backup. But Ubuntu doesn't remember that to manage it automatically. How to make it possible?

---

### Post by Toz on 2013-01-13
Yes, you can create a script and put it in /etc/pm/power.d. But first, you need to identify your backlight interface and be able to manually manipulate it. 

Open up a terminal, execute this command (it will report back on your backlight interfaces) and post back the results:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

Once we can manually manipulate the backlight interface, we'll create the script in the format of:
```
#!/bin/sh

. "${PM_FUNCTIONS}"

case $1 in
    true)  #laptop_mode_battery 
           #command to dim the screen brightness
    ;;
    false) #laptop_mode_ac
           #command to restore the screen brightness
    ;;
    *) exit $NA 
    ;;
esac

exit 0
```

---

