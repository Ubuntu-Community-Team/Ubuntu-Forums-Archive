---
title: "Wireless not working"
date: 2008-07-06
forum: General Help
---

### Post by 1qa2ws on 2008-07-06
I am running a wubi-installation on windows vista.

But I can't surf the web because it doesnt find the wireless card.


Here is my setup:


*Computer: ACPI x86-based PC. Intel/Advent, intel-processor CPU 530 1.73GHz

*Wirless card: under network adapters it says:
# SiS191 ethernet controller
# RealTek RTL8187B Wireless 802.1b/g 54Mbps USB 2.0 network adapter

*usb: SiS 7001 PCI to USB OPEN HOST CONTROLLER, standard enhanced PCI to... and some more
*router: belkin
*modem: billion
*generic multi card usb-device


Alternatives:
* wired connection - roaming mode enabled
* point to point connection - this method interface is not connected


Terminal:
sudo lshw -C network
gets:
description: ethernet interface
product 191 Gigabit Ethernet Adapter
and some more
driver sis190 driverversion=1.2

---

### Post by funkydan2 on 2008-07-07
I think you'll need to use the Windows drivers and ndiswrapper to get your wireless device to work.

Have a look at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) for info on how to do that.

---

### Post by ooobuntooo on 2008-07-09
Try cold-booting. Completely shut down the computer, instead of restarting and turn it on and boot into Ubuntu. See if that works.

---

