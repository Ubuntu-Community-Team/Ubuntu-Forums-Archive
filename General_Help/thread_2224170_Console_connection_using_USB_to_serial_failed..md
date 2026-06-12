---
title: "Console connection using USB to serial failed."
date: 2014-05-15
forum: General Help
---

### Post by gnrdeepak on 2014-05-15
Hi Team,



I have BAFO USB to serial converter connected to a Dell optiplex 3020. 
Minicom is installed.

Following changes were made-
:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    7.066425] usb 3-5: pl2303 converter now attached to ttyUSB0
[78815.850024] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[78848.066950] usb 3-2: pl2303 converter now attached to ttyUSB0

:~$ sudo modprobe usbserial vendor=0x067b product=0x2303

:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    7.066425] usb 3-5: pl2303 converter now attached to ttyUSB0



However, the connection fails although minicom configuration is correct. 
Same configuration has working on my laptop.

Please help


Thanks in advance

---

