---
title: "Please help with suspend"
date: 2007-09-12
forum: General Help
---

### Post by jrmontg on 2007-09-12
I have looked through others peoples post but have not found a solution that works for me.  I cannot get my laptop to suspend and come back up.  Can someone please assist.

---

### Post by reckless2k2 on 2007-09-12
need laptop specs. make..model...etc.

---

### Post by jrmontg on 2007-09-12
Sure this is a Fujitsu S7110

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:03.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
08:03.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
08:03.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
08:03.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 0

---

### Post by -Phi- on 2007-10-25
I have that same laptop, and suspend works for me but when it comes back up the screen is dark. Pressing Function+F7 usually works to turn on the backlight.

However, the brightness setting keys don't seem to work now that I've upgraded to Gutsy...

- Phi

---

### Post by -Phi- on 2007-10-30
Hey, just in case you're still looking for a solution, [this bug report]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/77212") should be helpful, especially [this comment]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/77212/comments/10"). Worked for me! (finally)

- Phi

---

