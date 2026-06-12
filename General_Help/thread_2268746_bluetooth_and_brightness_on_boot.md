---
title: "bluetooth and brightness on boot"
date: 2015-03-11
forum: General Help
---

### Post by Pedroski55 on 2015-03-11
Hi, I'd like to know how I can make Ubu 14.04 save my settings. I would like  the screen to boot dim, and bluetooth off. At the mo it always boots bluetooth on (I never use bluetooth) and screen full brightness.

Any tips please?

---

### Post by jeremy31 on 2015-03-11
```
sudo gedit  /etc/udev/rules.d/10-local.rules
```

and enter the following into the text editor
```
ACTION=="add", KERNEL=="hci0", RUN+="/usr/sbin/hciconfig hci0 down"
``` Save, exit program, and reboot

---

### Post by Pedroski55 on 2015-03-12
Thank you! I haven't tried it yet, what does it do? I am learning Chinese, but this is much more difficult. What does this control? Bluetooth! What about the brightness?

Tried that: brightness and bluetooth are unaffected, brightness is still full on, bluetooth is on.

Any other tips?

---

### Post by jeremy31 on 2015-03-14
The udev command should have been able to disable bluetooth on start but there is another method, since it didn't work we will delete it with ```
sudo rm [COLOR=#000000][FONT=Ubuntu Mono]/etc/udev/rules.d/10-local.rules
```[/FONT][/COLOR]

The other thing to try is ```
gksudo gedit /etc/rc.local
``` and add ```
rfkill block bluetooth
``` above the exit 0 line, then save, exit program and reboot

We will see if something can be done with the brightness, use the FN combo to get your brightness level where you want it then ```
for p in /sys/class/backlight/*; do echo $p; cat $p/brightness; cat $p/max_brightness; done
```

---

