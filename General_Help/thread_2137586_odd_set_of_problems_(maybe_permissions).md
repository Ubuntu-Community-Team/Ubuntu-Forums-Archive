---
title: "odd set of problems (maybe permissions)"
date: 2013-04-21
forum: General Help
---

### Post by brettfeeney on 2013-04-21
Hi,

I have installed ubuntu 12.10 (tried 64 and 32 bit versions) and no matter what I do, from straight vanilla install I can not sign in to Google Chrome Browser, nor can I clone a git repository ... lots of other things seem to work very well ... but after maybe 6 or 7 installs over the last 3 days, I have no idea what to do...

Chrome installs without error, then on the first run of it it will just time out when I go to sign in. Then subsequent runnings of the browser start at the login attempt, and then just silently fails, with no message that it even has failed. 

Cloning a Git repo just goes like 

Cloning into 'git'...
error: RPC failed; result=56, HTTP code = 0
fatal: The remote end hung up unexpectedly

I have tried changing the recommended buffer etc, to no avail.

I am not sure if they are connected in some permission issue I have, or what ... so I though I would trow it to the forum to see if there is anything glaringly wrong.

hwinfo --short .. produces this.

cpu:                                                            
                       Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz, 3000 MHz
                       Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz, 3000 MHz
graphics card:
                       nVidia GeForce 8600 GT
sound:
                       Intel 82801I (ICH9 Family) HD Audio Controller
storage:
                       Floppy disk controller
                       Intel 82801IB (ICH9) 2 port SATA IDE Controller
                       Intel 82801I (ICH9 Family) 2 port SATA IDE Controller
                       JMicron JMB368 IDE controller
network:
  eth0                 Realtek RTL-8110SC/8169SC Gigabit Ethernet
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
disk:
  /dev/fd0             Disk
  /dev/sda             SAMSUNG HD501LJ
  /dev/sdb             SAMSUNG HD501LJ
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
  /dev/sdb1            Partition
  /dev/sdb2            Partition
  /dev/sdb3            Partition
cdrom:
  /dev/sr0             PIONEER BD-RW   BDR-203
usb controller:
                       Intel 82801I (ICH9 Family) USB UHCI Controller #4
                       Intel 82801I (ICH9 Family) USB UHCI Controller #5
                       Intel 82801I (ICH9 Family) USB UHCI Controller #6
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #1
                       Intel 82801I (ICH9 Family) USB UHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #3
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #1
                       VIA VT82xxxxx UHCI USB 1.1 Controller
                       VIA VT82xxxxx UHCI USB 1.1 Controller
                       VIA USB 2.0
bios:
                       BIOS
bridge:
                       Intel 82G33/G31/P35/P31 Express DRAM Controller
                       Intel 82801I (ICH9 Family) PCI Express Port 1
                       Intel 82801I (ICH9 Family) PCI Express Port 5
                       Intel 82801 PCI Bridge
                       Intel 82801IB (ICH9) LPC Interface Controller
hub:
                       Linux 3.5.0-27-generic ehci_hcd EHCI Host Controller
                       Linux 3.5.0-27-generic uhci_hcd UHCI Host Controller
                       Linux 3.5.0-27-generic uhci_hcd UHCI Host Controller
                       Linux 3.5.0-27-generic uhci_hcd UHCI Host Controller
                       Linux 3.5.0-27-generic uhci_hcd UHCI Host Controller
                       Linux 3.5.0-27-generic uhci_hcd UHCI Host Controller
                       Linux 3.5.0-27-generic uhci_hcd UHCI Host Controller
                       Linux 3.5.0-27-generic ehci_hcd EHCI Host Controller
                       Linux 3.5.0-27-generic uhci_hcd UHCI Host Controller
                       Linux 3.5.0-27-generic ehci_hcd EHCI Host Controller
                       Linux 3.5.0-27-generic uhci_hcd UHCI Host Controller
memory:
                       Main Memory
firewire controller:
                       Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
  /dev/lp0             Parallel controller
                       Intel 82801I (ICH9 Family) SMBus Controller
                       Serial controller
                       Hauppauge WinTV Nova-DT

---

