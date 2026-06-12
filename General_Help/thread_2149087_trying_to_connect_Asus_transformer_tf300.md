---
title: "trying to connect Asus transformer tf300"
date: 2013-05-27
forum: General Help
---

### Post by Joe_Linux on 2013-05-27
I am trying to connect my Asus transformer tf300 to Ubuntu 12.04 to load some video files. Here is the result of lsusb

joe_linux@Fred:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:3880 Alcor Micro Corp. 
Bus 001 Device 004: ID 148f:2770 Ralink Technology, Corp. RT2770 Wireless Adapter
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 002: ID 1a86:7584 QinHeng Electronics CH340S
Bus 002 Device 005: ID 0b05:4c80 ASUSTek Computer, Inc. 
joe_linux@Fred:~$ 
Any thoughts on how I might access the pad ?


Thank you in advance

---

### Post by HiImTye on 2013-05-27
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
use Samba, it'll be far less headache
[ES File Explorer]("https://play.google.com/store/apps/details?id=com.estrongs.android.pop&hl=en") is a great overall file manager with Samba/GDrive/UbuntuOne/etc support

you might think about setting up [OpenSSH]("apt://openssh-server") as well to connect to your box from your tablet, in which case you will want [ConnectBot]("https://play.google.com/store/apps/details?id=org.connectbot&hl=en") and the [Hacker's Keyboard]("https://play.google.com/store/apps/details?id=org.pocketworkstation.pckeyboard&hl=en").

---

