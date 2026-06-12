---
title: "Using a udev rule to run a script that removes /dev/input/js0 and renames js1 to js0"
date: 2013-11-07
forum: General Help
---

### Post by takenover832 on 2013-11-07
My end goal is to disable/remove js0, which is using the stock/default input driver, which causes problems with my usb ps3 controller. I run sixad-raw which set's up js1, which uses a better driver. Once setup I want to remove js0 and rename js1 to js0. This will need done everytime the controller is plugged in, which is where the udev rules come into play.

The rule and script run. But some of the code within the script is not being executed correctly by udev. If I run the script manually, it work's fine.
To summarize. I want to remove "/dev/input/js0". I then want to rename "/dev/input/js1" to "/dev/input/js0". Currently it seems the rm and mv lines are having problems. Can anyone see corrections I need to make?

85-myrules.rules
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="054c", ATTR{idProduct}=="0268", RUN+="/usr/bin/startjoy1"
```

startjoy1 (has 0755 permissions)
```
#!/bin/bash

sudo sixad-raw /dev/hidraw2 &
sudo rm /dev/input/js0
sudo mv /dev/input/js1 /dev/input/js0
exit
```

---

### Post by takenover832 on 2013-11-08
I went a different route which seems to be working.
```
# Set joystick device priority 
KERNEL=="js?", ATTRS{name}=="SHENGHIC 2009/0708ZXW-V1Inc. PLAYSTATION(R)3Conteroller", NAME="input/js1", RUN+="/usr/bin/startjoy1"
KERNEL=="js?", ATTRS{name}=="PLAYSTATION(R)3 Controller (hidraw)", NAME="input/js0"
```

startjoy1
```
#!/bin/bash

sixad-raw /dev/hidraw2 &
exit
```

---

### Post by Pablo_San_Martn on 2014-06-29
I am having a similar problem here in Ubuntu 14.04. 

Where should I copy these files and with what name?

---

