---
title: "ACPI wakeup"
date: 2013-06-20
forum: General Help
---

### Post by Kostr on 2013-06-20
Hello! I am a BIOS developer and now i am trying to enable S3 wakeup from USB keyboard.
After boot, if i execute in terminal command «cat /proc/acpi/wakeup» i get:


Device    S-state      Status   Sysfs node
PCI0      S5     disabled  no-bus:pci0000:00
HDEF      S4     disabled  pci:0000:00:1b.0
RP01      S5     disabled  pci:0000:00:1c.0
RP02      S5     disabled  pci:0000:00:1c.1
RP03      S5     disabled  pci:0000:00:1c.2
RP04      S5     disabled  pci:0000:00:1c.3
RP05      S5     disabled  pci:0000:00:1c.4
RP06      S5     disabled  pci:0000:00:1c.5
USB1      S3     disabled  pci:0000:00:1d.0
USB2      S3     disabled  pci:0000:00:1d.1
USB3      S3     disabled  pci:0000:00:1d.2
USB4      S3     disabled  pci:0000:00:1d.3
EHC1      S3     disabled  pci:0000:00:1d.7
MODM      S4     disabled  
COMA      S3     disabled  pnp:00:08
COMB      S3     disabled  pnp:00:09

At my guess, current devices are devices from DSDT table with _PRW method. But for some reason wakeup for them disabled by default.
I can enable wakeup for keyboard (in my case it is USB1) with:


echo PCI0 > /proc/acpi/wakeup

echo USB1 > /proc/acpi/wakeup


I think, that these commands says to OS, that it should enable appropriate bits in ACPI GPE0_EN register before going to S3 (what bits exactly is defined in PCI0._PRW and USB1._PRW)

But this is not the end. I think OS power off USB controller when it goes to S3. To fix this i found device USB number from dmesg:


[     2.724374] input: LITEON Technology USB Multimedia Keyboard as  /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input6

And executed command «echo enabled > /sys/bus/usb/devices/2-2/power/wakeup»

And only now wakeup from USB works.

My question is, how i should change DSDT, to avoid all of these commands?

---

### Post by dino99 on 2013-06-20
hello "bios dev"

as you might already knows, the bios take control of the hardware only; there is no relationship with an OS here as the Os start way later. So if that DSDT table is not fully set or badly set, then an OS like linux report errors/warnings and be able to take control over the initial bios settings if the OS detect something wrong or not optimal. A tool like checkbox and/or fwts can help a lot to find the mismatch mess; dmidecode is also usefull, and "sudo lspci -vvnn" too.

---

