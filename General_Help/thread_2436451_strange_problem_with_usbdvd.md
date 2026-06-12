---
title: "strange problem with usb/dvd"
date: 2020-02-06
forum: General Help
---

### Post by brightstargiftss on 2020-02-06
Running Kubuntu 18.04, fully updated. I have a usb dock where I can insert a SATA drive. I have 2 DVD drives (DVD, Blu-ray). 

I put a drive in my usb dock and power it up. Computer recognizes it and mounts it. Dolphin can see it. 
I place a DVD in either drive. Drive spins up, lights flash for  few seconds then nothing. Computer doesn't see the DVD and doesn't mount it. 
Strange but here's the strangest part.
If I power down the dock, the computer sees the DVD and mounts it automatically.
I can then remount my usb dock and everything works.

If I plug ANY usb drive in to any usb port, the same thing happens.

No errors or messages that I can find. Dmesg shows only the mounting of the usb device. Everything looks good with lsusb and lshw.
I have rebooted the computer. Same behavior.

I would really appreciate ANY suggestions on where to look to solve the problem.
Thanks

```
/0                                   bus         F2A75M-D3H
/0/0                                 memory      64KiB BIOS
/0/23                                memory      8GiB System Memory
/0/23/0                              memory      DIMM [empty]
/0/23/1                              memory      DIMM Synchronous Unbuffered (Unregistered) [empty]
/0/23/2                              memory      DIMM Synchronous [empty]
/0/23/3                              memory      8GiB DIMM DDR3 Synchronous Unbuffered (Unregistered) 667 MHz (1.5 ns)
/0/2f                                memory      192KiB L1 cache
/0/30                                memory      4MiB L2 cache
/0/35                                processor   AMD A8-5600K APU with Radeon(tm) HD Graphics
/0/100                               bridge      Family 15h (Models 10h-1fh) Processor Root Complex
/0/100/0.2                           generic     Family 15h (Models 10h-1fh) I/O Memory Management Unit
/0/100/1                             display     Trinity [Radeon HD 7560D]
/0/100/1.1                           multimedia  Trinity HDMI Audio Controller
/0/100/4                             bridge      Family 15h (Models 10h-1fh) Processor Root Port
/0/100/4/0               enp1s0      network     RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/5                             bridge      Family 15h (Models 10h-1fh) Processor Root Port
/0/100/5/0               wlp2s0      network     AR93xx Wireless Network Adapter
/0/100/10                            bus         FCH USB XHCI Controller
/0/100/10/0              usb6        bus         xHCI Host Controller
/0/100/10/1              usb7        bus         xHCI Host Controller
/0/100/10.1                          bus         FCH USB XHCI Controller
/0/100/10.1/0            usb8        bus         xHCI Host Controller
/0/100/10.1/0/1                      generic     SnapScan Touch
/0/100/10.1/1            usb9        bus         xHCI Host Controller
/0/100/10.1/1/2          scsi6       storage     Pioneer Blu-ray Drive
/0/100/10.1/1/2/0.0.0    /dev/sr2    disk        BD-RW   BDR-XD05
/0/100/11                            storage     FCH SATA Controller [AHCI mode]
/0/100/12                            bus         FCH USB OHCI Controller
/0/100/12/1              usb3        bus         OHCI PCI host controller
/0/100/12/1/4                        input       USB Gaming Mouse
/0/100/12.2                          bus         FCH USB EHCI Controller
/0/100/12.2/1            usb1        bus         EHCI Host Controller
/0/100/12.2/1/1          scsi7       storage     JM20336 SATA, USB Combo
/0/100/12.2/1/1/0.0.0    /dev/sdd    disk        1500GB 41AS
/0/100/12.2/1/1/0.0.0/1  /dev/sdd1   volume      1396GiB EXT4 volume                                                                          
/0/100/12.2/1/2                      printer     ML-191x 252x Series                                                                          
/0/100/13                            bus         FCH USB OHCI Controller                                                                      
/0/100/13/1              usb4        bus         OHCI PCI host controller                                                                     
/0/100/13.2                          bus         FCH USB EHCI Controller                                                                      
/0/100/13.2/1            usb2        bus         EHCI Host Controller                                                                         
/0/100/13.2/1/3                      bus         USB2.0 Hub                                                                                   
/0/100/14                            bus         FCH SMBus Controller                                                                         
/0/100/14.2                          multimedia  FCH Azalia Controller                                                                        
/0/100/14.3                          bridge      FCH LPC Bridge                                                                               
/0/100/14.4                          bridge      FCH PCI Bridge                                                                               
/0/100/14.5                          bus         FCH USB OHCI Controller                                                                      
/0/100/14.5/1            usb5        bus         OHCI PCI host controller                                                                     
/0/101                               bridge      Family 15h (Models 10h-1fh) Processor Function 0                                             
/0/102                               bridge      Family 15h (Models 10h-1fh) Processor Function 1                                             
/0/103                               bridge      Family 15h (Models 10h-1fh) Processor Function 2                                             
/0/104                               bridge      Family 15h (Models 10h-1fh) Processor Function 3                                             
/0/105                               bridge      Family 15h (Models 10h-1fh) Processor Function 4                                             
/0/106                               bridge      Family 15h (Models 10h-1fh) Processor Function 5
/0/1                     scsi0       storage     
/0/1/0.0.0               /dev/sda    disk        1TB Hitachi HDT72101
/0/1/0.0.0/0             /dev/sda    disk        1TB 
/0/1/0.0.0/0/1           /dev/sda1   volume      23GiB EXT4 volume
/0/1/0.0.0/0/2           /dev/sda2   volume      3815MiB Linux swap volume
/0/1/0.0.0/0/3           /dev/sda3   volume      904GiB EXT4 volume
/0/2                     scsi1       storage     
/0/2/0.0.0               /dev/sdb    disk        1TB Hitachi HDT72101
/0/2/0.0.0/0             /dev/sdb    disk        1TB 
/0/2/0.0.0/0/1           /dev/sdb1   volume      931GiB EXT4 volume
/0/3                     scsi2       storage     
/0/3/0.0.0               /dev/cdrom  disk        BD Writer bd340i
/0/3/0.0.0/0             /dev/cdrom  disk        
/0/4                     scsi3       storage     
/0/4/0.0.0               /dev/sr1    disk        DVD RW AD-7200S
/0/5                     scsi5       storage     
/0/5/0.0.0               /dev/sdc    disk        1TB Hitachi HDT72101
/0/5/0.0.0/0             /dev/sdc    disk        1TB 
/0/5/0.0.0/0/1           /dev/sdc1   volume      931GiB EXT4 volume

```

---

### Post by mörgæs on 2020-02-09
Have you checked if updated BIOS firmware is available?

---

