---
title: "External harddrive"
date: 2007-05-23
forum: General Help
---

### Post by hanch on 2007-05-23
I have searched the forums and google for this issue but have not found anything that has helped me.  I am not able to mount my external usb hdd in ubuntu.  It works fine in windows and had been working in linux until today.   It would always automatically mount and bring up the shortcut on the desktop but nothing today.

Any suggestions?

---

### Post by taurus on 2007-05-23
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by hanch on 2007-05-23
```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9447    75882996   83  Linux
/dev/hdb2            9448        9729     2265165    5  Extended
/dev/hdb5            9448        9729     2265133+  82  Linux swap / Solaris

```

---

### Post by taurus on 2007-05-23
Did you connect your external harddrive to your machine and is it on?

---

### Post by hanch on 2007-05-23
That mounted my 80 gig windows partition, but didn't do anything with the 160 gig external usb drive.

---

### Post by hanch on 2007-05-23
Yes, the drive is connected and turned on.  The power light on the drive is on.  And when I reboot into windows it works fine.  I have had this drive for about a month and this is the first problem I've had.

---

### Post by taurus on 2007-05-23
Maybe you want to boot into Windows and defrag and scan your external drive first.  Then, boot back into Ubuntu and see if Ubuntu can read it now.

```
sudo fdisk -l
```

---

### Post by feister on 2007-05-23
I am not sure if this help you but it sure did for me: remove the internal hdd and boot then see if it shows up in BIOS. My WinDOZ XP is on my internal hdd of my lappy and I have an external 500G hdd(for Ubuntu and other distros of LINUX ) and during installation of feisty I removed the internal to be 100% sure that nothing happens and everything worked fine.

---

### Post by hanch on 2007-05-23
I rebooted to windows ran defrag on the disk, scanned it (no errors found).

sudo fdisk -l returned 
```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9447    75882996   83  Linux
/dev/hdb2            9448        9729     2265165    5  Extended
/dev/hdb5            9448        9729     2265133+  82  Linux swap / Solaris
```

---

### Post by hanch on 2007-05-23
the bios recognizes my usb devices fine.  

any other suggestions?

---

### Post by logos34 on 2007-05-23
Is it detected with  

**lshw **
or
**lsusb**
?

---

### Post by hanch on 2007-05-23
where do i find that?

---

### Post by logos34 on 2007-05-23
run it in a terminal like fdisk

better to use  
**sudo lshw**

For lsusb it should appear as usb
and under one of the *usb: headings as "mass storage" with lshw

here's mine:
$ lsusb
**Bus 002 Device 004: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter**
Bus 002 Device 002: ID 0ace:1215 ZyDAS 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 001 Device 001: ID 0000:0000  

$sudo lshw
.....

*-usb:0
                description: Generic USB device
                product: USB2.0 WLAN
                vendor: ZyDAS
                physical id: 2
                bus info: usb@2:2
                version: 48.10
                capabilities: usb-2.00
                configuration: driver=zd1211b maxpower=500mA speed=480.0MB/s
[B]*-usb:1
                description: Mass storage device
                product: USB TO IDE
                vendor: Genesys Logic, Inc.
                physical id: 6
                bus info: usb@2:6
                version: 0.33
                capabilities: usb-2.00 scsi
                configuration: driver=usb-storage maxpower=96mA speed=480.0MB/s[/B]
     *-ide:0
          description: IDE interface
          product: MCP51 IDE

---

### Post by hanch on 2007-05-23
```
$ sudo lsusb
Bus 003 Device 004: ID 0781:7420 SanDisk Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:8604 Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  

```

the external hdd is not listed

```
$ sudo lshw
  *-usb:0
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: iomemory:e9087000-e9087fff irq:16
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Optical USB Mouse
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@1:2
                   version: 3.40
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: iomemory:e9082000-e9082fff irq:17
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb
                   description: Printer
                   product: Deskjet 5400 series
                   vendor: HP
                   physical id: 3
                   bus info: usb@2:3
                   version: 1.00
                   serial: TH571142DR047N
                   capabilities: usb-2.00 bidirectional
                   configuration: driver=usblp maxpower=2mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@00:02.2
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: iomemory:e9083000-e90830ff irq:18
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: Sansa e280
                   vendor: SanDisk
                   physical id: 4
                   bus info: usb@3:4
                   version: 7.20
                   serial: 00000000-00000000-4978b387-d010f615-00000000
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s

```

---

### Post by hanch on 2007-05-23
Okay,

I just unplugged my mp3 player from the computer and the external hdd mounted automatically.  How can I get both to work at once since this seems to be where the problem was?

---

### Post by logos34 on 2007-05-23
> ** *-usb UNCLAIMED**
                   description: Generic USB device
                   product: Sansa e280
                   vendor: SanDisk
                   physical id: 4
                   bus info: usb@3:4
                   version: 7.20
                   serial: 00000000-00000000-4978b387-d010f615-00000000
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s

maybe there was a problem caused by not unmounting the player before unplugging it (even though it's probably set hot-plugable), which in turn caused a problem with usb2 controller...just guessing here.  

try rebooting

---

### Post by hanch on 2007-05-23
problem solved,

changed the usb mode of the player and everything works again.

thanks for all of the help.

---

