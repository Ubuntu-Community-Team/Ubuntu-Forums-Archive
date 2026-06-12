---
title: "Computer will not wakeup using mouse or keyboard"
date: 2014-06-03
forum: General Help
---

### Post by ksanger on 2014-06-03
Hello;  I'm running Ubuntu 12.04 for a long time.  Recently, within the last week, my computer began to not wakeup using the mouse or keyboard.  I have brightness and lock to turn off the screen after 1 hour.  Power is set to don't suspend.  I am using a wireless Logitech mouse and keyboard which is seen on USB Bus 004.  I have seen the Device # change after resuming or rebooting.  The power button lets me resume using a momentary press.  

I have tried putting the word "enabled" into the file /sys/bus/usb/devices/4-1/power/wakeup.  That worked one time but then after resuming the file contained the word "disabled" and resume would not work twice in a row.  

Included below are the results of lspci and lsusb.

me@myPC:/sys/bus/usb/devices$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port G)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
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
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde XT [Radeon HD 7770 GHz Edition]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
my@myPC:/sys/bus/usb/devices$ 

me@myPC:/sys/bus/usb/devices$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
my@myPC:/sys/bus/usb/devices$

---

### Post by tgalati4 on 2014-06-03
Install *acpitool* and post the output of:

```
acpitool -w
```

If Bus 004 is disabled, then enable it with *acpitool* and test again.

Also check your BIOS and make sure you have checked the setting "Allow USB devices to wake".  That will also keep power to the USB bus.  Test the bus with another device to see if you have power to that port when the machine is put to sleep.  If not, then check all the ports and see if any remain powered during sleep.

---

### Post by ksanger on 2014-06-03
I think I fixed it by following instructions here, [http://ubuntuforums.org/showthread.php?t=1968487](http://ubuntuforums.org/showthread.php?t=1968487), to edit /etc/udev/rules.d/90-keyboardwakeup.rules.  I used the following line: 

SUBSYSTEM=="usb", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c52b" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"

Installing acpitool and running acpitool -w gives me the following:
me@myPC:~$ acpitool -w
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. SBAZ      S4    *disabled  pci:0000:00:14.2
  2. UAR1      S4    *disabled  pnp:00:0a
  3. P0PC      S4    *disabled  pci:0000:00:14.4
  4. UHC1      S4    *enabled   pci:0000:00:12.0
  5. UHC2      S4    *enabled   pci:0000:00:12.2
  6. USB3      S4    *enabled   pci:0000:00:13.0
  7. UHC4      S4    *enabled   pci:0000:00:13.2
  8. USB5      S4    *enabled   pci:0000:00:16.0
  9. UHC6      S4    *enabled   pci:0000:00:16.2
  10. UHC7      S4    *enabled   pci:0000:00:14.5
  11. PE20      S4    *disabled  
  12. PE21      S4    *disabled  
  13. PE22      S4    *disabled  
  14. PE23      S4    *disabled  
  15. PC02      S4    *disabled  pci:0000:00:02.0
  16. PC04      S4    *disabled  pci:0000:00:04.0
  17. PC05      S4    *disabled  
  18. PC06      S4    *disabled  
  19. PC07      S4    *disabled  pci:0000:00:07.0
  20. PC09      S4    *disabled  
  21. PC0A      S4    *disabled  
  22. PC0B      S4    *disabled  
  23. PC0C      S4    *disabled  
  24. PC0D      S4    *disabled  
  25. PWRB      S4    *enabled   
me@myPC:~$

This is weird as I do not see USB4 as being enabled.  There is nothing on USB3 and USB5.  man acpitool states to use -W x where x is the device # to enable or disable it.  But USB4 is not in the list?  Perhaps because I'm running a desktop and not a laptop?

The /etc/udev/rules.d/90-keyboardwakeup.rules file is working though:

me@myPC:~$ cat /sys/bus/usb/devices/4-1/power/wakeup
enabled
me@myPC:~$

Here you can see that only USB4 has a device on it.
me@myPC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
me@myPC:~$

I have been using Ubuntu 12.04 LTS for many years and have not required the udev rule file up until now.  I'm hoping it fixes my issue though as I've had numerous times over the past week where I come back and could not log back in.  I like to leave stuff out, and you know how you can have a lot open at once.

I have an Asus M5A97 with American MEgatrends Inc. Version 0901.  I did not see an option to wake from USB.  I do have USB legacy support enabled.

me@myPC:~$ sudo dmidecode | more
# dmidecode 2.11
SMBIOS 2.7 present.
55 structures occupying 2512 bytes.
Table at 0x000EED90.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 0901
    Release Date: 11/24/2011
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 4096 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 4.6

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: To be filled by O.E.M.
    Product Name: To be filled by O.E.M.
    Version: To be filled by O.E.M.
    Serial Number: To be filled by O.E.M.
    UUID: 85BE9500-B83F-11DC-AF47-C86000D9D4E7
    Wake-up Type: Power Switch
    SKU Number: To be filled by O.E.M.
    Family: To be filled by O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASUSTeK COMPUTER INC.
    Product Name: M5A97
    Version: Rev 1.xx
    Serial Number: MT7022044104990
    Asset Tag: To be filled by O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To be filled by O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

---

