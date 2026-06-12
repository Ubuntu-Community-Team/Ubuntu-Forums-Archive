---
title: "USB2 device behaving like it's USB1"
date: 2006-11-28
forum: General Help
---

### Post by fulat2k on 2006-11-28
Hi folks,

I'm using a USB2 pendrive connected to a USB2 port.  lsmod shows that ehci and uhci modules are loaded.  However, when I perform a file copy, the speed slows down to a crawl.  

May I know if I've missed anything?


Thanks.

---

### Post by syadnom on 2006-11-28
try and rmmod the ehci and then try again. if that doesnt work try ro rmmod the uhci and try the drive, then if that doesnt work try to rmmod BOTH the ehci and uhci and try the drive again.

your USB1.1 drivers may be being used so if you remove all the usb modules the right module may load as need OR you might find that the ehci module is fighting you..

worth a shot anyway.

---

### Post by fulat2k on 2006-11-28
First tried rmmod uhci.  No go.  Then I rmmod ehci as well.  Even worse, the USB stick doesn't even get detected :)

---

### Post by syadnom on 2006-11-28
my hope was that the modules would autoload for the USB as needed but it seems not.  have you tried all of your usb ports?  you may have 2 USB controllers or the controller you have may not have any USB2 drivers in the kernel.

---

### Post by wieman01 on 2006-11-28
Just to confirm... Having the same issue when upgrading to more recent kernel versions. Have locked my kernel version for the time being, but would love to see the problem resolved. USB 2.0 works with the current one.

---

### Post by fulat2k on 2006-11-29
The USB port I tried works like a charm under Win2k.  Will see if the other USB port exhibits the same problem.  But I don't think it's likely.

wieman01: Which kernel r u using?  I'm on 2.6.17-10-generic (Kubuntu 6.10)

---

### Post by wieman01 on 2006-11-29
I am using 2.6.15-23... Still on Dapper. But I get into trouble when upgrading to the current (most recent) version. Transfer rate is confined to 2.0 MB/sec (= USB 1.0).

---

### Post by syadnom on 2006-11-29
which USB chipset do you guys have??

---

### Post by wieman01 on 2006-11-29
That's mine:
>  description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:ec00-ec1f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-23-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s

---

### Post by syadnom on 2006-11-29
its something about how the module is loading, see the line
"configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s"

it is set to USB1 speed.  this may be a line you can add to modules.conf for this modules..i gotta run to work right now but i might be able to find something for you tonight.

i have this chipset in an intel board and edgy loads the driver properly and gives me full speed.

---

### Post by wieman01 on 2006-11-29
> **syadnom said:**
> its something about how the module is loading, see the line
"configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s"

it is set to USB1 speed.  this may be a line you can add to modules.conf for this modules..i gotta run to work right now but i might be able to find something for you tonight.

i have this chipset in an intel board and edgy loads the driver properly and gives me full speed.
Thanks, man. Only happens when I upgrade my current kernel 2.6.15-23-386 to the most recent version... This version is alright, but after an upgrade it runs at 2.0 MB/sec. Pretty annoying. Would be nice to know what I need to do after loading the new kernel version.

---

### Post by fulat2k on 2006-11-29
Just found out something strange.  When I have ehci_hcd loaded, usbview shows that the host controller is on high speed (480Mb/s).  But when uhci_hcd is loaded, usbview shows that the host controller is on the full speed (12Mb/s).  

Anyone getting the same results?

---

### Post by wieman01 on 2006-11-29
Mmm... That is indeed strange. I'll test that tonight (my time)... And get back to you then. Interesting finding.

---

### Post by machia on 2006-12-03
I have similar problems and I haven't found anywhere a solution..

Is it possible to tell the kernel to use ehci-drivers instead uhci-drivers so that my usb2.0-ports have the proper speed? No the default is uhci and it cant handle usb2.0 high-speed..

Anyone got ideas?

> **fulat2k said:**
> Just found out something strange.  When I have ehci_hcd loaded, usbview shows that the host controller is on high speed (480Mb/s).  But when uhci_hcd is loaded, usbview shows that the host controller is on the full speed (12Mb/s).  

Anyone getting the same results?

Me. Although it seems to work random when my ext-hd decides to use ehci-drivers..

---

### Post by bodymind on 2006-12-08
Hi,
when i plugged in my usb2.0 mass storage i get this errors on dmesg:

[17187262.368000] usb 4-2: new high speed USB device using ehci_hcd and address 21
[17187263.124000] usb 4-2: new high speed USB device using ehci_hcd and address 22
[17187263.996000] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17187264.108000] usb 4-2: new high speed USB device using ehci_hcd and address 23
[17187264.980000] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17187265.092000] usb 4-2: new high speed USB device using ehci_hcd and address 24
[17187265.500000] usb 4-2: device not accepting address 24, error -71
[17187265.612000] usb 4-2: new high speed USB device using ehci_hcd and address 25
[17187266.020000] usb 4-2: device not accepting address 25, error -71

but if i remove the module uhci_hcd with (rmmod uhci_hcd) and let only ehci_hcd working my usb2.0 mass storage works fine :) but when i do this.. my modem that needs USB1.1 stops working... any ideas?

by the way.. here's my output when i remove uhci_hcd module and turn the player on:

[17188645.092000] uhci_hcd 0000:00:10.0: USB bus 1 deregistered
[17188645.092000] ACPI: PCI interrupt for device 0000:00: 10.0 disabled
[17188654.964000] usb 4-2: new high speed USB device using ehci_hcd and address 26
[17188655.104000] usb 4-2: configuration #1 chosen from 1 choice
[17188655.104000] scsi1 : SCSI emulation for USB Mass Storage devices
[17188655.104000] usb-storage: device found at 26
[17188655.104000] usb-storage: waiting for device to settle before scanning
[17188660.104000] usb-storage: device scan complete
[17188660.104000]   Vendor: USB 2.0   Model: Storage Device    Rev: 0100
[17188660.104000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17188660.112000] SCSI device sda: 39063024 512-byte hdwr sectors (20000 MB)
[17188660.112000 ] sda: Write Protect is off
[17188660.112000] sda: Mode Sense: 08 00 00 00
[17188660.112000] sda: assuming drive cache: write through
[17188660.120000] SCSI device sda: 39063024 512-byte hdwr sectors (20000 MB)
[17188660.120000] sda: Write Protect is off
[17188660.120000] sda: Mode Sense: 08 00 00 00
[17188660.120000] sda: assuming drive cache: write through
[17188660.120000]  sda: sda1
[17188660.132000] sd 1:0:0:0: Attached scsi disk sda
[17188660.132000] sd 1:0:0:0: Attached scsi generic sg0 type 0


and then i just have to: fdisk -l
mount /dev/sda1 /mnt/pen
and everything is fine... |: any ideas?


i've found out that if i plug-in my usb mass storage, before ubuntu loads i get it working under USB2.0 =o really odd thing.. i thing it's alien thing.

---

