---
title: "Ubuntu Bluetooth"
date: 2016-06-08
forum: General Help
---

### Post by Alex_Rodgers on 2016-06-08
I had posted this on stack overflow, but seeing as a month or more has gone by without a reply, here is the link: [http://askubuntu.com/questions/772450/ubuntu-16-04-bluetooth](http://askubuntu.com/questions/772450/ubuntu-16-04-bluetooth)

So I have ubuntu gnome 16.04 installed. I was using bluetooth to connect to my headset before I upgrade. [This]("http://i.stack.imgur.com/EhXV1.png"), is what I see. The Dell card is from my other laptop that isn't even turned on, and the hesh 2 wireless is my headset. I can [click]("http://i.stack.imgur.com/rhpCv.png")  on the headset and it gives me the option to connect, or remove device.  If I click to connect, the switch just slides over and back again, and  if I click to remove the device, that window closes, but does nothing. I  cannot even find new bluetooth devices. How can I fix this?

please just reply here

---

### Post by jeremy31 on 2016-06-08
Welcome to the forums.  I am not sure if I can help with this card as they can be difficult.  Please post the results of the following from terminal
```
lsusb; dmesg | egrep -i 'blue|firm'; hciconfig -a
```

---

### Post by Alex_Rodgers on 2016-06-08
```
alex@alex-ubuntu:~$ lsusb; dmesg | egrep -i 'blue|firm'; hciconfig -a
Bus 002 Device 004: ID 03f0:0423 Hewlett-Packard HS-COMBO Cardreader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[    0.186595] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[   30.859774] iwl3945 0000:10:00.0: loaded firmware version 15.32.2.9
[ 6731.328016] tg3 0000:18:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update
[ 6731.388019] tg3 0000:18:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update
[ 6731.448013] tg3 0000:18:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update


```
why would the firmware all of the sudden have a bug, it worked before my update, it has really been **BUGGING **me that I cant use blue tooth. I don't even know where to begin to update firmware.

---

### Post by jeremy31 on 2016-06-09
The bluetooth device isn't even found as the Dell 370 should show in USB results even though it is a card on the motherboard.  The firmware errors are for the ethernet card

You should file a bug report against package linux.  There is a [guide to filing bug reports](http://ubuntuforums.org/showthread.php?t=1011078)

Be sure to mention that it did work prior to installing 16.04

---

### Post by Alex_Rodgers on 2016-06-09
> **jeremy31 said:**
> The bluetooth device isn't even found as the Dell 370 should show in USB results even though it is a card on the motherboard.  The firmware errors are for the ethernet card

You should file a bug report against package linux.  There is a [guide to filing bug reports]("http://ubuntuforums.org/showthread.php?t=1011078")

Be sure to mention that it did work prior to installing 16.04

that dell bluetooth card is for my other laptop, that was shut down at the time, it is all frozen, I have an hp laptop with a hp bluetooth card, it is like the bluetooth settings are frozen permanently, even after restart.

---

