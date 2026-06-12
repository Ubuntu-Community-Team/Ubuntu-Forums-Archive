---
title: "Disabling parallel port"
date: 2007-06-25
forum: General Help
---

### Post by pseudonym on 2007-06-25
I set up a lite version of Ubuntu based on the [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") installation method, on this machine -

IBM PC 300PL
550MHz Pentium III
256MB PC100 RAM
Intel 440BX Chipset
80GB Seagate HDD
Sony CD-RW drive
32MB Nvidia TNT2 AGP video card
3Com 3c509B ISA network card
Intel Etherexpress Pro Onboard LAN
Silicon Image 680 PCI IDE controller card
Ensoniq AudioPCI sound card
PCI USB2.0 card

I don't have any devices which use the serial or parallel legacy ports so I disabled them in the BIOS, to free up those IRQs. But Ubuntu is still detecting the parallel port and loading modules for it - ```
 cat /proc/interupts
CPU0       
  0:    4516472    XT-PIC-XT        timer
  1:      10406    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:     665132    XT-PIC-XT        eth0
  5:          1    XT-PIC-XT        parport0
  6:          3    XT-PIC-XT        floppy
  7:          5    XT-PIC-XT        uhci_hcd:usb1
  8:          3    XT-PIC-XT        rtc
  9:     716195    XT-PIC-XT        acpi, uhci_hcd:usb2, nvidia
 10:      29266    XT-PIC-XT        libata, uhci_hcd:usb3
 12:     401611    XT-PIC-XT        i8042
 14:       2370    XT-PIC-XT        ehci_hcd:usb4, Ensoniq AudioPCI
 15:         51    XT-PIC-XT        ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

```
```
 lsmod | grep lp
lp                     12452  0 
parport                36936  2 lp,parport_pc
```
I tried blacklisting the parallel port modules but the kernel ignores it. I also tried adding 'parport=0' to the kernel command line but it doesn't do anything.

The obvious solution is to build a custom kernel without parallel port support, but I want to see if there's anything else that can be done first, or at least find out what's causing the parallel port to still be detected.

Thanks.

---

