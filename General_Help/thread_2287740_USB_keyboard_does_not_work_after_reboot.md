---
title: "USB keyboard does not work after reboot"
date: 2015-07-21
forum: General Help
---

### Post by majurarainer on 2015-07-21
I am using Ubuntu 14.04 LTS recently installed on a new desktop machine. When I reboot the keyboard will not let type in my logon so the mouse is usually (but not always) OK. The light on the keyboard is on, so it's getting power. Key board is responsive in BIOS and works in selecting options in GRUB before Ubuntu desktop login screen. I can plug another keyboard into another USB port  and this will usually works to open a terminal. If I then sudo shutdown -h now and boot up again (after unplugging the other keyboard) everything is fine for that session. Next time I boot up after the computer was shut down for some time the same problem may occur again, but the problem is intermittent.  Grateful for any ideas, while there are some posts on keyboard problems out there nothing seems to quite match that behaviour.

---

### Post by majurarainer on 2015-07-22
This also happens when the computer suspends. When keyboard is working:

~$ lsusb
Bus 003 Device 002: ID 04f9:02e9 Brother Industries, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 003: ID 046d:082c Logitech, Inc. 
Bus 008 Device 002: ID 2109:3431  
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Vladlenin5000 on 2015-07-22
It often has to do with BIOS/UEFI settings. Some may show erratic behavior with anything else but (USB) legacy = auto.

---

### Post by majurarainer on 2015-07-23
Ok BIOS was set to USB legacy - enabled, have changed to AUTO but still same behavior. Last time it was the mouse not the keyboard. Unplugging the mouse and plugging it back in reconnects the device.

some additional info:
**lspci**
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Oland PRO [Radeon R7 240]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
02:00.0 USB controller: VIA Technologies, Inc. Device 3483 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)

lsusb -t
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/1p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/4p, 480M
        |__ Port 2: Dev 3, If 0, Class=Audio, Driver=snd-usb-audio, 480M
        |__ Port 2: Dev 3, If 1, Class=Audio, Driver=snd-usb-audio, 480M
        |__ Port 2: Dev 3, If 2, Class=Video, Driver=uvcvideo, 480M
        |__ Port 2: Dev 3, If 3, Class=Video, Driver=uvcvideo, 480M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/4p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/5p, 12M
    |__ Port 4: Dev 7, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 5: Dev 6, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 5: Dev 6, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/5p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    |__ Port 3: Dev 2, If 0, Class=Printer, Driver=usblp, 480M
    |__ Port 3: Dev 2, If 1, Class=Vendor Specific Class, Driver=, 480M
    |__ Port 3: Dev 2, If 2, Class=Vendor Specific Class, Driver=, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/5p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/5p, 480M

---

### Post by Bashing-om on 2015-07-23
majurarainer; Hello;

In my bios is an option " enable plug and play " As ubuntu is a plug and play operating system, this functionality must be enabled also.
All I know to do too, is the changes in bios .

[INDENT][INDENT]it all starts in bios
[/INDENT][/INDENT]

---

### Post by majurarainer on 2015-07-24
Other usb devices seem to be ok

---

### Post by Bashing-om on 2015-07-26
majurarainer; Hummm ...

Swap in another known good keyboard ?

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by majurarainer on 2015-07-27
I edited the /etc/default/grub file and change the GRUB_CMDLINE_LINUX_DEFAULT line to add the usbcore.autosuspend=-1 option:
Save file and closed, Updated grub and rebooted.

Now ~$ cat /sys/module/usbcore/parameters/autosuspend gives me -1.

This has reduced the problem, but it still occurs occasionally. Very frustrating.

---

### Post by majurarainer on 2015-07-27
Bashing-on, thanks but it happens with a spare keyboard as well as with my wireless keyboard

---

### Post by majurarainer on 2015-07-29
After a few days of testing it appears that turning off autosuspend has not fixed the problem. Unplugging the keyboard and plugging it back in everytime I boot up is a poor solution. Is there anything else anyone can think of? It does not appear to be hardware related as the problem occurs with different keyboards and also with the mouse.

---

### Post by majurarainer on 2015-07-30
[COLOR=#111111][FONT=Ubuntu]reinstall or install input device drivers might fix it?[/FONT][/COLOR]

---

### Post by majurarainer on 2015-08-09
Problem still bugging me. Sometimes its the keyboard sometimes its the mouse. Unplugging and plugging it back in in seems to fix it for the session. Any ideas anyone?

---

### Post by majurarainer on 2015-08-11
This is been going on for some weeks now with no solution in sight. Is this a problem to do with Trusty Tahr? do I need to try a different version? Anywhere outside of this forum I should go? This is a shared computer and I am not always there to plug things in and out and/or reboot several times to fix the problem. I truly would appreciate some help, I am trying to learn more about Ubuntu but this has got me beat.

---

### Post by majurarainer on 2015-08-31
after mouse does not work and I unplug and plug in agin I get the following additional output from dmesg:
[  223.647689] usb 5-4: USB disconnect, device number 2
[  251.748094] usb 5-4: new low-speed USB device number 4 using ohci-pci
[  252.119531] usb 5-4: New USB device found, idVendor=093a, idProduct=2510
[  252.119538] usb 5-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  252.119543] usb 5-4: Product: USB Optical Mouse
[  252.119547] usb 5-4: Manufacturer: PixArt
[  252.127154] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.0/0003:093A:2510.0003/input/input17
[  252.127541] hid-generic 0003:093A:2510.0003: input,hidraw2: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:13.0-4/input0

---

### Post by matt_taylor2 on 2015-09-22
Had the same problem for months now, tried everything listed here and elsewhere to no avail, 
*** Finally tried in BIOS under usb settings to Disable EHCI Handoff, seems to have fixed it

---

