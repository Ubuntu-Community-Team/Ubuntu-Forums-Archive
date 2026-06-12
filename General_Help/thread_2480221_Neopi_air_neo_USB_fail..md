---
title: "Neopi air neo USB fail."
date: 2022-10-22
forum: General Help
---

### Post by josephchrzempiec on 2022-10-22
Hello, I tried to wire up a Female usb ort to the neopi air neo and when I plugged in a usb flash drive I get this from it.

pi@NanoPi-NEO-Air:~$ [  143.887742] usb usb4-port1: Cannot enable. Maybe the USB                                                                                                              cable is bad?
[  145.082746] usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
[  145.592751] usb usb7-port1: Cannot enable. Maybe the USB cable is bad?
[  146.317744] usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
[  147.302730] usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
[  147.309407] usb usb4-port1: unable to enumerate USB device
[  147.517762] usb usb7-port1: Cannot enable. Maybe the USB cable is bad?
[  149.082818] usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
[  149.972767] usb usb7-port1: Cannot enable. Maybe the USB cable is bad?
[  149.997800] usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
[  151.232722] usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
[  152.317759] usb usb7-port1: Cannot enable. Maybe the USB cable is bad?
[  152.324396] usb usb7-port1: unable to enumerate USB device
pi@NanoPi-NEO-Air:~$ [  143.887742] usb usb4-port1: Cannot enable. Maybe the USB                                                                                                              cable is bad?




If I do a lsusb I get this from it.

root@NanoPi-NEO-Air:~# lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@NanoPi-NEO-Air:~#

I'm trying to get the usb torun But I have no clue. I never had this type of board or problem before. Can someone please help me to figure this problem out?

Joseph

---

### Post by josephchrzempiec on 2022-10-23
Hello, I manage to now see the USB. I rebooted and it let me see the USB flash drive.

---

### Post by MAFoElffen on 2022-10-23
You still have the pinout wrong
USB-A            Board
#1 - Red     - #1 - 5V
#2 - Green - #2 - D+
#3 - White  - #3 - D-
#4 - Black  -  GND

---

### Post by MAFoElffen on 2022-10-23
So you are running Ubuntu 20.04 or 22.04 Core now?

---

### Post by josephchrzempiec on 2022-10-23
Yes But Now after i shut down the neopi air and restarted it back up after the third time. I'm getting garbage all over the serial monitor. open on com3 speed 15200.

[IMG]http://deletethis.info/neopiairneo.png[/IMG]



However If i close out putty and reopen it back up and go to speed 9600 it works fine. But if I send a reboot once more I get that same garbage screen. And if I close putty and open a new session at 115200 it works again.

Joseph

---

### Post by josephchrzempiec on 2022-10-27
Hello everything seem to be okay now. After update and reboot usb and serial seems to work now.

---

### Post by MAFoElffen on 2022-10-27
So is this "Solved" now?

If so, then please use the "thread tools" link in the upper right of this page to mark the thread as "Solved" so the others using various SBC's can find our answer to solve their similar issues.

---

### Post by josephchrzempiec on 2022-11-30
Hello this is solved now. I&#8217;m able to ssh and do things on it as well as updated the os. Thank you all for the help and support.

---

