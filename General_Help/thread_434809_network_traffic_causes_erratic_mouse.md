---
title: "network traffic causes erratic mouse"
date: 2007-05-06
forum: General Help
---

### Post by mseewald on 2007-05-06
Hello,

First of all, I would like to thank everybody who has made Feisty Fawn possible. This is a fantastic Linux distribution for the Desktop!!

I have a bizarre phenomenon going on when network traffic is high. In those occasions the mouse movements become erratic and slow. It seems Linux gives a higher priority to network than to my mouse.

System:
[INDENT]CPU: Intel E6300 Dual Core with 2GB RAM
Mainboard: Gigabyte P965-DS4 with onboard Gigabit adapter
Mouse: Sigma M400, USB plug, wireless (non-bluetooth), optical
Network: 100 MBit LAN[/INDENT]

From xorg.conf:
[INDENT]Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection[/INDENT]

From /proc/bus/usb/devices:
[INDENT]T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0425 ProdID=f102 Rev= 0.01
S:  Manufacturer=G-Tech CHINA
S:  Product=U+P Wireless Mouse  
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms[/INDENT]

Situations with "high network traffic":
- 3 or more parallel downloads with Firefox (several 100 kb/s)
- torrent downloads at high speed (several 100 kb/s)

Is there anything I can do? Could I increase the mouse buffer? Or use another mouse driver?

Thanks & kind regards,
Michael

---

### Post by rai4shu2 on 2007-05-06
Anything you can do to reduce noise between your network and the pick up for the mouse?

---

### Post by mseewald on 2007-05-06
Sorry, I don't get it. What do you mean by noise? This is not related to interference of bluetooth and WLAN. I use  a cable for the LAN.

---

### Post by rai4shu2 on 2007-05-06
No, but your mouse is wireless. It seems to me that you're getting noise from somewhere. If not from the LAN, I don't see where the interference could be coming from.

---

