---
title: "how to connect to wifi"
date: 2013-01-01
forum: General Help
---

### Post by archit1993 on 2013-01-01
Hi,
i am using ubuntu for the first time.i was trying to connect to wifi,but no wireless networks were being shown,even when i am sitting next to a wifi router and it is being shown on windows....do i need to change some settings or download something?
plz help
thanks

---

### Post by 2F4U on 2013-01-01
Depending on your network card, you may need drivers not included in the default install. Did you look for additional drivers (you would need to connect through wired ethernet to be able to do that)? Did you apply all available updates after installing Ubuntu? What version of Ubuntu are you running?

---

### Post by archit1993 on 2013-01-01
i have ubuntu 12.10 and i ran sudo apt-get update from terminal,what else do i need to update and how to know which driver should i download?
thanks

---

### Post by archit1993 on 2013-01-01
on typing lspci in terminal,i get the following

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9200M GS] (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

---

### Post by 2F4U on 2013-01-01
The drivers for your broadcom network b43 network card should be available through the additional drivers application, which can be accessed through the Software sources program:


[http://techspalace.blogspot.de/2012/10/additional-drivers-in-ubuntu-1210.html](http://techspalace.blogspot.de/2012/10/additional-drivers-in-ubuntu-1210.html)
[http://www.howopensource.com/2012/10/find-additional-drivers-in-ubuntu-12-10/](http://www.howopensource.com/2012/10/find-additional-drivers-in-ubuntu-12-10/)

---

### Post by iMac71 on 2013-01-01
you might try the solution I indicated in the following post:
[http://ubuntuforums.org/showthread.php?p=12432106#post12432106](http://ubuntuforums.org/showthread.php?p=12432106#post12432106)

---

