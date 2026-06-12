---
title: "Wireless not working"
date: 2007-09-13
forum: General Help
---

### Post by Seiya55 on 2007-09-13
ok, i know there are other forums in which this is discussed and i have read many already.
but non of them seem to help.

What i have done now is get all three packets from "synaptic manager" on wireless networking. Still it doesnt work. it seems not to recieve any signal. Im tiered of using ehernet cable and not being able to work from other places. 
can anyone please help me?

---

### Post by prince_niceguy on 2007-09-13
what is the card you are using?

can you post the result of the following?

> lspci

with knowledge of card you have it would be easy to debug and help you.

---

### Post by super.rad on 2007-09-13
Some more information would be helpful such as which version of ubuntu you are using and what your wireless card is.
To find out what chipset your wireless card is type into a terminal
```
lspci
``` If it's PCI
or
```
lsusb
``` if it's usb.
Post the output here and then people can try and help

EDIT: Looks like i was beaten to it.

---

### Post by Seiya55 on 2007-09-13
[PHP]molina@molina-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)0000:0b:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)molina@molina-laptop:~$
[/PHP]

this is what "lspci"  gave me.
and its Ubuntu 6.06.
thanks for the help guys.

---

### Post by Lylepalooza on 2007-09-13
Can you also please try the USB output as mentioned in one of the above posts. Your wireless card doesn't seem to be listed in the PCI output so I am assuming that it is USB? Is that correct?

---

