---
title: "Unclaimed ethernet controller and driver won't DL"
date: 2016-04-01
forum: General Help
---

### Post by andy176 on 2016-04-01
I am brand-spanking new to Linux and have installed Lubuntu 15.10 on an older emachine desktop that had Vista (gross) on it. The installation process warned that Lubuntu couldn't be updated during installation because no internet connection was available. The Ethernet worked previously on Vista, so I assume when old OS was removed it deleted the ethernet card's driver. Upon installation no networks were available and after looking through several other threads I have been unable to install the drivers for the ethernet controller (Intel Pro/100 VE). 

I DLed this driver onto a flash drive but couldn't install it: [https://downloadcenter.intel.com/download/17289/Network-Device-and-Driver-Information-Utility-for-Linux-](https://downloadcenter.intel.com/download/17289/Network-Device-and-Driver-Information-Utility-for-Linux-)

Here are the outputs for a few standard queries:

**********************************************************************************************************************
lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
06:01.0 Communication controller: Conexant Systems, Inc. Device 2f40
06:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
****************
sudo ifconfig -a
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:480 errors:0 dropped:0 overruns:0 frame:0
TX packets:480 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:38208 (38.2 KB) TX bytes:38208 (38.2 KB)
**********************************************************************************************
cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
**********************************************************************************************
dmesg | grep -e bcm
No Output
**********************************************************************************************
lshw -C Network
WARNING: you should run this program as super-user.
*-network UNCLAIMED 
description: Ethernet controller
product: PRO/100 VE Network Connection
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:06:08.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=32 maxlatency=56 mingnt=8
resources: memory:50010000-50010fff ioport:1000(size=64)
**********************************************************************************************************************************
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 3 [8086:27d4] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 4 [8086:27d6] (rev 01)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 [8086:27e0] (rev 01)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 [8086:27e2] (rev 01)
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge [8086:27b0] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 01)
06:01.0 Communication controller [0780]: Conexant Systems, Inc. Device [14f1:2f40]
06:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1094] (rev 01)

Any help is greatly appreciated!

---

### Post by mörgæs on 2016-04-02
Hi, welcome to the fora.

It's surprising that a wired Intel network card does not work right away. I only found a few examples of similar problems: 
[http://ubuntuforums.org/showthread.php?t=1708888](http://ubuntuforums.org/showthread.php?t=1708888)

Does this help?

---

### Post by Yellow Pasque on 2016-04-02
I would look in dmesg for clues (especially anything related to e100).
What happens if you try to modprobe the module manually?
```
sudo modprobe -v e100
```

---

### Post by andy176 on 2016-04-02
Thanks for the replies:

Here's what the BIOS shows for ACPI IRQ

dmesg | grep IRQ
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] NR_IRQS:2304 nr_irqs:456 16
[    0.145358] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.145489] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.145618] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12)
[    0.145744] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.145872] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12)
[    0.145998] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.146129] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[    0.146258] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11 12)
[    0.148504] PCI: Using ACPI for IRQ routing
[    0.150268] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.200063] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled

I didn't see anything specifically about bugs or failures.

Here is something interesting for general dmesg:

1.726943] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.726949] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.751671] e100 0000:06:08.0 0000:06:08.0 (uninitialized): EEPROM corrupted
[    1.751743] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    1.781468] [drm] Initialized drm 1.1.0 20060810
[    1.784355] e100: probe of 0000:06:08.0 failed with error -11

Thanks again!

---

### Post by andy176 on 2016-04-02
Also, no output for:

[COLOR=#000000][INDENT]sudo modprobe -v e100
[/INDENT]
[/COLOR]
[INDENT]
[/INDENT]

---

### Post by SeijiSensei on 2016-04-02
Try running "sudo apt-get install linux-firmware" and see if that helps.

---

### Post by andy176 on 2016-04-02
sudo apt-get install linux-firmware
Reading package lists... Done
Building dependency tree      
Reading state information... Done
linux-firmware is already the newest version.
linux-firmware set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Thanks for the suggestions.

---

### Post by Yellow Pasque on 2016-04-02
Here is the error we are concerned with:
```
[ 1.751671] e100 0000:06:08.0 0000:06:08.0 (uninitialized): EEPROM corrupted
```

A quick Google shows that the EEPROM probably isn't corrupted (especially if it worked the last time you used Vista) and there is a workaround if this is the case.

Try this:
```
sudo modprobe -r e100
sudo modprobe -v e100 eeprom_bad_csum_allow=1
```

If it works (or modprobe complains about removing the module), then run the following command and reboot:
```
echo "options e100 eeprom_bad_csum_allow=1" | sudo tee /etc/modprobe.d/e100.conf
```

---

### Post by andy176 on 2016-04-05
Sorry for the delay.  My rude students keep returning the work that I assign them, which I then have to grade.

I tried the recommended commands and got this:

laura@laura-T5224:~$ sudo modprobe -r e100
[sudo] password for laura:
laura@laura-T5224:~$ sudo modprobe -v e100 eeprom_bad_csum_allow=1
insmod /lib/modules/4.2.0-16-generic/kernel/drivers/net/mii.ko
insmod /lib/modules/4.2.0-16-generic/kernel/drivers/net/ethernet/intel/e100.ko eeprom_bad_csum_allow=1 eeprom_bad_csum_allow=1
laura@laura-T5224:~$ echo "options e100 eeprom_bad_csum_allow=1" | sudo tee /etc/modprobe.d/e100.conf
options e100 eeprom_bad_csum_allow=1



I rebooted and still saw no network available so I re-ran dmesg and here is the relevant excerpt:

 1.703699] [drm] Initialized drm 1.1.0 20060810
[    1.746542] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.746548] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.769725] e100 0000:06:08.0 0000:06:08.0 (uninitialized): EEPROM corrupted
[    1.820378] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    1.836644] e100: probe of 0000:06:08.0 failed with error -11

Seems same as before.  I did a bit of Googling about it but couldn't make sense of what I ran across.  Such a pain to try and fix networking issues...because most solutions involve downloads.

Is there something else to do with the modprobe, or is it time to update the BIOS?



Thank again for all suggestions!

---

### Post by Yellow Pasque on 2016-04-06
One last thing to try and then I'm out of ideas (unless a BIOS update also updates your ethernet chip):
```
sudo modprobe -r e100
sudo modprobe -v e100 use_io=1 eeprom_bad_csum_allow=1
```

---

### Post by andy176 on 2016-04-10
Same lack of result as before.  I will post the outcome of BIOS upgrade attempt.


Thanks again for the effort!

---

