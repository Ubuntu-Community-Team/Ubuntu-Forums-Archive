---
title: "Wammu does not accept bluetooth device"
date: 2008-06-21
forum: General Help
---

### Post by wtkwhite on 2008-06-21
Hi everyone.

I am a Debian Etch user and am trying to get my Nokia 6300 to connect to Wammu over a bluetooth dongle.

I have bluez-python, bluez-utils, bluetooth, kdebluetooth, et cetera installed. When I ask Wammu to scan for my phone, it detects that the device is there, but does not recognise it as a phone:

Starting /dev/ttyS0 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303']
Starting /dev/ttyS1 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303']
Starting /dev/ttyS2 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303']
Scanning for bluetooth devices using PyBluez
Checking 00:19:B7:B5:47:C5 (Dvorak 6300i) - ['bluephonet', 'bluefbus', 'bluerfgnapbus', 'blueat', 'bluerfphonet', 'bluerffbus', 'bluerfat']
Bluetooth device scan completed
Finished /dev/ttyS0 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303']
Finished /dev/ttyS1 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303']
Finished /dev/ttyS2 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303']
Finished 00:19:B7:B5:47:C5 (Dvorak 6300i) - ['bluephonet', 'bluefbus', 'bluerfgnapbus', 'blueat', 'bluerfphonet', 'bluerffbus', 'bluerfat']
All finished, found 0 phones

Can anyone help?

---

### Post by mirkone on 2008-10-05
Hello,
i have the same Problem with my 6300i on this Page you can see that the 6300 mobile is running with wammu this is the wammu logfile:

have a good weekend,
mirkone

---

