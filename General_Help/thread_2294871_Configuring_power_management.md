---
title: "Configuring power management"
date: 2015-09-14
forum: General Help
---

### Post by amukher on 2015-09-14
I recently started using the Trusty Tahr 64 bit Ubuntu minimal installation. One of the things I need to do is configure power management.
Using the powertop command gave me he following output:

> Bad           Wireless Power Saving for interface wlan0                                                              
   Bad           NMI watchdog should be turned off
   Bad           Enable SATA link power Managmenet for host4
   Bad           Enable SATA link power Managmenet for host5
   Bad           Enable SATA link power Managmenet for host3
   Bad           Enable SATA link power Managmenet for host0
   Bad           Enable SATA link power Managmenet for host1
   Bad           VM writeback timeout
   Bad           Enable SATA link power Managmenet for host2
   Bad           Autosuspend for USB device USB2.0-CRW [Generic]
   Bad           Autosuspend for USB device USB Optical Mouse [PixArt]
   Bad           Autosuspend for USB device Dell USB Entry Keyboard [Dell]
   Bad           Autosuspend for USB device USB Portable HDD [Dell]
   Bad           Runtime PM for PCI Device Intel Corporation 4th Gen Core Processor Integrated Graphics Controller
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [
   Bad           Runtime PM for PCI Device Intel Corporation HM86 Express LPC Controller
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller
   Bad           Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2
   Good          Enable Audio codec power management
   Good          Autosuspend for USB device USB2.0 Hub [3-6]
   Good          Autosuspend for unknown USB device 1-1 (8087:8008)
   Good          Autosuspend for unknown USB device 2-1 (8087:8000)
   Good          Autosuspend for USB device EHCI Host Controller [usb1]
   Good          Autosuspend for USB device EHCI Host Controller [usb2]
   Good          Autosuspend for USB device xHCI Host Controller [usb3]
   Good          Autosuspend for USB device xHCI Host Controller [usb4]
   Good          Runtime PM for PCI Device Qualcomm Atheros QCA8172 Fast Ethernet
   Good          Runtime PM for PCI Device Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
   Good          Runtime PM for PCI Device Qualcomm Atheros AR9485 Wireless Network Adapter
   Good          Runtime PM for PCI Device Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller
   Good          Runtime PM for PCI Device Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
   Good          Wake-on-lan status for device p2p1
   Good          Wake-on-lan status for device wlan0
   Good          Using 'ondemand' cpufreq governor

As you can see, there are a number of lines marked as **BAD**. I then enabled powersave by through **sudo pm-powersave true**. After this, I again used powertop to check the status. But I find that there is no difference at all. There are a number of scripts in /usr/lib/pm-utils/power.d which should have taken effect.

Where should I start looking to solve the problem?

---

### Post by kerry_s on 2015-09-14
why?
"Bad" just means it's not supported. if you read what the bad is, you'll see a good for that same device via other means.

i see no issue here, looks like its doing what its suppose to.

---

