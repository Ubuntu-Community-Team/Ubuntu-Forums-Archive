---
title: "Bluetooth NOT able to detect ANYTHING!"
date: 2023-04-07
forum: General Help
---

### Post by raderall on 2023-04-07
yeah I've tried everything, Installing blue man, dmesg, ect and it will not detect my bluetooth Razer Atheris Mouse or my Serafim Lazer Keyboard or anything else I may not be attempting to use around. I have had an ASUS z97 pro gamer motherboard for years and I've noticed even with Windows 11 that it has alot of problems with bluetooth. I have a dongle in the back and I tried keeping my PC off for nearly 2 minutes. Maybe there's a conflicting bios setting?

---

### Post by ActionParsnip on 2023-04-07
What is the output of:
```

sudo dmesg | grep -i blue; lsb_release -a; uname -a; lsusb; lspci; sudo rfkill list

```

---

### Post by raderall on 2023-04-07
[    6.800256] Bluetooth: Core ver 2.22
[    6.800278] NET: Registered PF_BLUETOOTH protocol family
[    6.800279] Bluetooth: HCI device and connection manager initialized
[    6.800283] Bluetooth: HCI socket layer initialized
[    6.800285] Bluetooth: L2CAP socket layer initialized
[    6.800289] Bluetooth: SCO socket layer initialized
[    6.927658] Bluetooth: hci0: CSR: Setting up dongle with HCI ver=9 rev=0810; LMP ver=9 subver=2312; manufacturer=10
[    6.927662] Bluetooth: hci0: CSR: Unbranded CSR clone detected; adding workarounds and force-suspending once...
[    6.927664] Bluetooth: hci0: CSR: Couldn't suspend the device for our Barrot 8041a02 receive-issue workaround
[    6.927668] Bluetooth: hci0: HCI Delete Stored Link Key command is advertised, but not supported.
[    6.927669] Bluetooth: hci0: HCI Read Default Erroneous Data Reporting command is advertised, but not supported.
[    6.927671] Bluetooth: hci0: HCI Set Event Filter command not supported.
[    7.036831] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    7.036834] Bluetooth: BNEP filters: protocol multicast
[    7.036837] Bluetooth: BNEP socket layer initialized
[    8.809146] Bluetooth: RFCOMM TTY layer initialized
[    8.809154] Bluetooth: RFCOMM socket layer initialized
[    8.809158] Bluetooth: RFCOMM ver 1.11
[   85.428823] Bluetooth: hci0: command 0x200c tx timeout
[   85.428829] Bluetooth: hci0: failed to disable LE scan: status 0x1f
[   86.484203] Bluetooth: hci0: CSR: Setting up dongle with HCI ver=9 rev=0810; LMP ver=9 subver=2312; manufacturer=10
[   86.484209] Bluetooth: hci0: CSR: Unbranded CSR clone detected; adding workarounds and force-suspending once...
[   86.484213] Bluetooth: hci0: CSR: Couldn't suspend the device for our Barrot 8041a02 receive-issue workaround
[   86.484219] Bluetooth: hci0: HCI Delete Stored Link Key command is advertised, but not supported.
[   86.484221] Bluetooth: hci0: HCI Read Default Erroneous Data Reporting command is advertised, but not supported.
[   86.484223] Bluetooth: hci0: HCI Set Event Filter command not supported.
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.10
Release:	22.10
Codename:	kinetic
Linux MasterPC 5.19.0-38-generic #39-Ubuntu SMP PREEMPT_DYNAMIC Fri Mar 17 17:33:16 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
Bus 002 Device 002: ID 8087:8001 Intel Corp. Integrated Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 008: ID 05e3:0745 Genesys Logic, Inc. Logilink CR0012
Bus 003 Device 010: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 006: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 003 Device 009: ID 1532:0062 Razer USA, Ltd Atheris
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x8 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (2) I218-V
00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d0)
00:1c.6 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 7 (rev d0)
00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
00:1f.0 ISA bridge: Intel Corporation Z97 Chipset LPC Controller
00:1f.2 RAID bus controller: Intel Corporation SATA Controller [RAID mode]
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] (rev c7)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]
02:00.0 USB controller: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller (rev 03)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 04)
06:00.0 Non-Volatile memory controller: Intel Corporation SSD 660P Series (rev 03)
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by MAFoElffen on 2023-04-07
Do you have Razor's OpenRazor driver installed?
```

sudo add-apt-repository ppa:openrazer/daily
sudo apt update
sudo apt install openrazer-meta

```
This is the driver that your computer needs to use any of Razor's bluetooth devices...

---

### Post by raderall on 2023-04-07
I installed that and it still won't detect my mouse or Serafim or anything in the bluetooth manager, It did list an error that it didn't like my Secure boot setting though.

quick edit. I switched the setting and still nothing working. let me see what is different or improved on my Windows 11 boot.

---

### Post by DuckHook on 2023-04-07
Did you reboot after installing driver? You must do so for the driver module to load.

---

### Post by raderall on 2023-04-08
Yep still no dice. Maybe that Serafim is only compatible with phones somehow though and theres a button combination I need to google to press for my mouse when I'm engaging all that. or maybe I need to remove it's wifi dongle when trying to tell it to switch to bluetooth mode?

---

### Post by raderall on 2023-04-10
Yeah there is a button combination but the thing is still no dice, and I owned another Asus X97 Pro gamer prior to this and could not get bluetooth working at all. I have a usb dongle and it's detected but it does not see any bluetooth hardware at all. Someone somewhere a long time ago says they knew someone who know someone that had this and they had to get a M2. Slot Bluetooth card to get all this to work. There has to be a a conflicting bios setting I think. But good luck getting help from them on reddit or anywhere unless you want to completely take your giant pc off your desk and completely move everything around and get in there to retrieve the Serial number to get anywhere talking to them or there people.

---

### Post by raderall on 2023-04-14
Anyone have any idea on a bios setting catagory to change in the bios? Or should I ask a motherboard forum or group for this? Anyone know a good site or forum or discord or should I just post in computer hardware on reddit this problem and that I'm sure it's a bios setting and that I cannot use the /Asus as they're that bad a name to get support from?

---

### Post by jeremy31 on 2023-04-15
The Cambridge Silicon Radio Bluetooth devices have had issues with Linux for some time and it seems they either work or they don't

---

### Post by dragonfly41 on 2023-04-15
Took me sometime to realise that my Logitech MX Keys (keyboard) and MX Master 3S (mouse) had three Bluetooth profiles (1, 2, 3) which are found on the keyboard above insert, Home, Page up keys, and at the mouse are found underside. When I use Windows, Linux or Tablet I have to remember to switch between 1, 2, 3. Otherwise keyboard/mouse do not function.

---

### Post by raderall on 2023-04-16
Can you recommend a brand that works perfectly with Linux? or some third party drivers to install to fix this?

---

### Post by jeremy31 on 2023-04-16
I have had good luck with IOgear GBU521 and the Edimax BT-8500 seems to work in Ubuntu 22.04 and 22.10

---

### Post by him610 on 2023-04-18
This worked on my wife's laptop (BIOS: 2012) Xubuntu 22.04
Kinivo USB Bluetooth Adapter for PC BTD400 (Bluetooth 4.0 Dongle Receiver, Low Energy) - Compatible with Windows 11/10/8.1/8/7, Raspberry Pi, **Linux**, MacOS, Laptop & Headphones
[https://www.amazon.com/gp/product/B007Q45EF4/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1]("https://www.amazon.com/gp/product/B007Q45EF4/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1")

---

