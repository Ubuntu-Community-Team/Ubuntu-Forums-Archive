---
title: "usb not working on ubuntu"
date: 2012-10-15
forum: General Help
---

### Post by Rakeshvijayan on 2012-10-15
Hi friends

I pluged my mobile phone in my laptop for charging .on that time my external hard disk also plugged in that time suddenly harddisk is down and no other usb is not dictated in sub ports ............ 
This is the message I got ,hard is plugged but light is not on hard disk 
 sudo fdisk -l
> rivaus@rivaus:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d45e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   945868799   472933376   83  Linux
/dev/sda2       945870846   976771071    15450113    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       945870848   960856063     7492608   83  Linux
/dev/sda6       960858112   976771071     7956480   82  Linux swap / Solaris 
dmesg | grep  -i USB
> rivaus@rivaus:~$ dmesg | grep  -i USB
[    0.683634] usbcore: registered new interface driver usbfs
[    0.683642] usbcore: registered new interface driver hub
[    0.683666] usbcore: registered new device driver usb
[    1.221417] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.221487] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.240011] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.240188] hub 1-0:1.0: USB hub found
[    1.240297] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.259979] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.260147] hub 2-0:1.0: USB hub found
[    1.260197] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.260206] uhci_hcd: USB Universal Host Controller Interface driver
[    1.260243] usbcore: registered new interface driver libusual
[    1.551581] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.684102] hub 1-1:1.0: USB hub found
[    1.795198] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.927585] hub 2-1:1.0: USB hub found
[    1.998950] usb 1-1.3: new high-speed USB device number 3 using ehci_hcd
[    2.242775] usb 2-1.2: new low-speed USB device number 3 using ehci_hcd
[    2.314665] usb 2-1.2: device descriptor read/64, error -32
[    2.490460] usb 2-1.2: device descriptor read/64, error -32
[    2.666158] usb 2-1.2: new low-speed USB device number 4 using ehci_hcd
[    2.738031] usb 2-1.2: device descriptor read/64, error -32
[    2.913769] usb 2-1.2: device descriptor read/64, error -32
[    3.089520] usb 2-1.2: new low-speed USB device number 5 using ehci_hcd
[    3.496626] usb 2-1.2: device not accepting address 5, error -32
[    3.568588] usb 2-1.2: new low-speed USB device number 6 using ehci_hcd
[    3.975943] usb 2-1.2: device not accepting address 6, error -32
[    3.976117] hub 2-1:1.0: unable to enumerate USB device on port 2
[    4.048022] usb 2-1.6: new full-speed USB device number 7 using ehci_hcd
[    6.879828] usb 2-1.2: new low-speed USB device number 8 using ehci_hcd
[    6.951727] usb 2-1.2: device descriptor read/64, error -32
[    7.071798] hub 2-1:1.0: unable to enumerate USB device on port 2
[    7.399055] usb 2-1.2: new low-speed USB device number 9 using ehci_hcd
[    7.470950] usb 2-1.2: device descriptor read/64, error -32
[    7.646682] usb 2-1.2: device descriptor read/64, error -32
[    7.822424] usb 2-1.2: new low-speed USB device number 10 using ehci_hcd
[    7.894316] usb 2-1.2: device descriptor read/64, error -32
[    8.014385] hub 2-1:1.0: unable to enumerate USB device on port 2
[    8.245793] usb 2-1.2: new low-speed USB device number 11 using ehci_hcd
[    8.317684] usb 2-1.2: device descriptor read/64, error -32
[    8.437758] hub 2-1:1.0: unable to enumerate USB device on port 2
[    8.637204] usb 2-1.2: new low-speed USB device number 12 using ehci_hcd
[    8.653429] hub 2-1:1.0: unable to enumerate USB device on port 2
[   10.882092] hub 2-1:1.0: unable to enumerate USB device on port 2
[   11.225467] usb 2-1.2: new low-speed USB device number 14 using ehci_hcd
[   11.241515] hub 2-1:1.0: unable to enumerate USB device on port 2
[   11.696762] usb 2-1.2: new low-speed USB device number 15 using ehci_hcd
[   11.712978] hub 2-1:1.0: unable to enumerate USB device on port 2
[   11.928248] usb 2-1.2: new low-speed USB device number 16 using ehci_hcd
[   11.944729] hub 2-1:1.0: unable to enumerate USB device on port 2
[   12.511782] hub 2-1:1.0: unable to enumerate USB device on port 2
[   12.860485] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   12.862086] usbcore: registered new interface driver btusb
[   12.876382] input: TOSHIBA Web Camera - MP as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input4
[   12.876497] usbcore: registered new interface driver uvcvideo
[   12.876499] USB Video Class driver (1.1.1)
[   26.242972] usb 2-1.1: new low-speed USB device number 18 using ehci_hcd
[   26.314886] usb 2-1.1: device descriptor read/64, error -32
[   26.490634] usb 2-1.1: device descriptor read/64, error -32
[   26.666373] usb 2-1.1: new low-speed USB device number 19 using ehci_hcd
[   26.738270] usb 2-1.1: device descriptor read/64, error -32
[   26.913972] usb 2-1.1: device descriptor read/64, error -32
[   27.089706] usb 2-1.1: new low-speed USB device number 20 using ehci_hcd
[   27.496979] usb 2-1.1: device not accepting address 20, error -32
[   27.568996] usb 2-1.1: new low-speed USB device number 21 using ehci_hcd
[   27.976262] usb 2-1.1: device not accepting address 21, error -32
[   27.976371] hub 2-1:1.0: unable to enumerate USB device on port 1


I dont know what happen on my laptop what should I do , I need data on e-harddisk 
hope some one will help me 

Thanks

---

