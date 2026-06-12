---
title: "Proper way to disable bluetooth?"
date: 2013-05-04
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-05-04
using 13.04 raring ringtail

disabling it saved a good % of my boot time, and i have never used any bluetooth hardware, so i clearly don't need it
i disabled bluetooth via /etc/modprobe.d/blacklist.conf
```
# disable Bluetooth
blacklist bnep
blacklist btusb
blacklist bluetooth
```
What is the proper way? currently i get this
```
~$ dmesg | grep bluetooth
[    8.035538] init: bluetooth main process (1063) terminated with status 1
[    8.035552] init: bluetooth main process ended, respawning
[    8.054221] init: bluetooth main process (1129) terminated with status 1
[    8.054236] init: bluetooth main process ended, respawning
[    8.068414] init: bluetooth main process (1167) terminated with status 1
[    8.068430] init: bluetooth main process ended, respawning
[    8.080701] init: bluetooth main process (1193) terminated with status 1
[    8.080717] init: bluetooth main process ended, respawning
[    8.096227] init: bluetooth main process (1224) terminated with status 1
[    8.096244] init: bluetooth main process ended, respawning
[    8.168351] init: bluetooth main process (1249) terminated with status 1
[    8.168367] init: bluetooth main process ended, respawning
[    8.192971] init: bluetooth main process (1354) terminated with status 1
[    8.192988] init: bluetooth main process ended, respawning
[    8.215690] init: bluetooth main process (1404) terminated with status 1
[    8.215708] init: bluetooth main process ended, respawning
[    8.234050] init: bluetooth main process (1437) terminated with status 1
[    8.234064] init: bluetooth main process ended, respawning
[    8.255914] init: bluetooth main process (1464) terminated with status 1
[    8.255931] init: bluetooth main process ended, respawning
[    8.272435] init: bluetooth main process (1504) terminated with status 1
[    8.272451] init: bluetooth respawning too fast, stopped
```

---

### Post by ArthurBorsboom on 2013-07-08
Did you solve this (minor) issue?
And if so, how? :)

Thanks!

---

### Post by holycow131415 on 2013-07-09
use rfkill, or some of these suggestions. [http://askubuntu.com/questions/131684/how-to-boot-with-bluetooth-turned-off](http://askubuntu.com/questions/131684/how-to-boot-with-bluetooth-turned-off)

---

