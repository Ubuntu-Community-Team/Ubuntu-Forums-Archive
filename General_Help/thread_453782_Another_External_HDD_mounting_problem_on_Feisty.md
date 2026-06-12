---
title: "Another External HDD mounting problem on Feisty"
date: 2007-05-24
forum: General Help
---

### Post by evil baz on 2007-05-24
OK I had searched in all the forum and I hadn't found an answer to this problem so I will post a similar question but with more reference of what is happening:

I was working great on edgy and I saw that Feisty was available to upgrade, so I upgrade and everything was working great till I connected my 2 external USB hard drives.

one of them a Firelite, its working without problem,it doesn't need an adapter to get energy (ac adapter).

The other one a a USB to IDE HDD WD, it was working on edgy, but now it don't appear on the entire system, I do fdisk and this is what I get when i connect it:

```
Disco /dev/hda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1        4660    37431418+  83  Linux
/dev/hda2            4661        4865     1646662+   5  Extendida
/dev/hda5            4661        4865     1646631   82  Linux swap / Solaris

Disco /dev/sda: 80.0 GB, 80060424192 bytes
255 cabezas, 63 sectores/pista, 9733 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        9733    78180291    c  W95 FAT32 (LBA)

```

as you can see detect the main internal HDD and the Firelite HDD but not the enclosed HDD, then I disconnected it and runned "udevmonitor", then I reconnected it and this is what it show:

```

UDEV the event which udev sends out after rule processing
UEVENT the kernel uevent

UEVENT[1180047577.277401] add      /devices/pci0000:00/0000:00:10.3/usb4/4-2/4-2.3 (usb)
UEVENT[1180047577.277549] add      /class/usb_endpoint/usbdev4.11_ep00 (usb_endpoint)
UEVENT[1180047577.278067] add      /devices/pci0000:00/0000:00:10.3/usb4/4-2/4-2.3/4-2.3:1.0 (usb)
UEVENT[1180047577.278088] add      /class/scsi_host/host18 (scsi_host)
UEVENT[1180047577.278103] add      /class/usb_endpoint/usbdev4.11_ep81 (usb_endpoint)
UEVENT[1180047577.278118] add      /class/usb_endpoint/usbdev4.11_ep02 (usb_endpoint)
UEVENT[1180047577.278132] add      /class/usb_device/usbdev4.11 (usb_device)
UDEV  [1180047577.328613] add      /devices/pci0000:00/0000:00:10.3/usb4/4-2/4-2.3 (usb)
UDEV  [1180047577.375302] add      /class/usb_endpoint/usbdev4.11_ep81 (usb_endpoint)
UDEV  [1180047577.384267] add      /class/usb_endpoint/usbdev4.11_ep02 (usb_endpoint)
UDEV  [1180047577.391202] add      /class/usb_endpoint/usbdev4.11_ep00 (usb_endpoint)
UDEV  [1180047577.869078] add      /devices/pci0000:00/0000:00:10.3/usb4/4-2/4-2.3/4-2.3:1.0 (usb)
UDEV  [1180047577.874032] add      /class/scsi_host/host18 (scsi_host)
UDEV  [1180047577.999696] add      /class/usb_device/usbdev4.11 (usb_device)
UEVENT[1180047587.842056] remove   /class/usb_endpoint/usbdev4.11_ep81 (usb_endpoint)
UEVENT[1180047587.842139] remove   /class/usb_endpoint/usbdev4.11_ep02 (usb_endpoint)
UEVENT[1180047587.849323] remove   /class/scsi_host/host18 (scsi_host)
UEVENT[1180047587.849410] remove   /devices/pci0000:00/0000:00:10.3/usb4/4-2/4-2.3/4-2.3:1.0 (usb)
UEVENT[1180047587.849430] remove   /class/usb_device/usbdev4.11 (usb_device)
UEVENT[1180047587.849446] remove   /class/usb_endpoint/usbdev4.11_ep00 (usb_endpoint)
UEVENT[1180047587.849464] remove   /devices/pci0000:00/0000:00:10.3/usb4/4-2/4-2.3 (usb)
UDEV  [1180047587.855625] remove   /class/usb_endpoint/usbdev4.11_ep81 (usb_endpoint)
UDEV  [1180047587.865493] remove   /class/usb_endpoint/usbdev4.11_ep02 (usb_endpoint)
UDEV  [1180047587.868518] remove   /class/scsi_host/host18 (scsi_host)
UDEV  [1180047587.910807] remove   /devices/pci0000:00/0000:00:10.3/usb4/4-2/4-2.3/4-2.3:1.0 (usb)
UDEV  [1180047587.942517] remove   /class/usb_endpoint/usbdev4.11_ep00 (usb_endpoint)
UDEV  [1180047587.984875] remove   /devices/pci0000:00/0000:00:10.3/usb4/4-2/4-2.3 (usb)
UDEV  [1180047587.989057] remove   /class/usb_device/usbdev4.11 (usb_device)


```

Hope someone can help me, cuz I had recently moved completely to Ubuntu, and now with this Im desperate, thanks in advance.

---

### Post by disposable on 2007-05-24
Disconnect the drive and reboot (humor me). When you're back up, plug in the drive and then tail /var/log/messages. If you see your drive referenced and it's not mounted, try to pmount the drive:

$ pmount /dev/sdd

Let us know what happens.

---

### Post by evil baz on 2007-05-25
ok sorry I was absent tha last hours but now I'm back, after done what you said I do exactly what you told and this is what I found:

```

May 25 09:41:09 DARKMOON gconfd (root-5875): El servidor GConf no está en uso, cerrándolo.
May 25 09:41:09 DARKMOON gconfd (root-5875): Finalizando
May 25 09:41:32 DARKMOON kernel: [ 4052.819503] usb 4-2.3: new high speed USB device using ehci_hcd and address 4
May 25 09:41:32 DARKMOON kernel: [ 4052.912666] usb 4-2.3: configuration #1 chosen from 1 choice
May 25 09:41:32 DARKMOON kernel: [ 4052.913135] scsi1 : SCSI emulation for USB Mass Storage devices
**May 25 09:41:43 DARKMOON kernel: [ 4063.460418] scsi 1:0:0:0: scsi: Device offlined - not ready after error recovery**
May 25 09:41:43 DARKMOON kernel: [ 4063.461229] usb 4-2.3: USB disconnect, address 4

```

the bolded part is what it worry the most, because it says that is an error, but after done this I connected to a windows pc and it works perfect.

Any suggestion?

---

### Post by disposable on 2007-05-25
I found this searching for "Device offlined - not ready after error recovery" ubuntu usb hard drive:

[http://www.neowin.net/forum/lofiversion/index.php/t556286.html](http://www.neowin.net/forum/lofiversion/index.php/t556286.html)

It looks like a hardware compatibility issue. Try different USB drivers and keep searching for issues with your particular hardware. Maybe contact the vendor? Sorry I wasn't more help.

---

### Post by evil baz on 2007-05-25
Thanks for your help disposable ^^.

The weird thing is that when I was using edgy  it was working perfect, and also one thing I forgot to tell is that before that I uninstall Windows what I do to make Feisty to recognize this particular HDD was first boot on Feisty, then if I saw that the HDD wasn't mounted then I boot on Windows and plugin the HDD then Windows read it and all that stuff, and then again reboot to Feisty and by Magic the HDD was recognized by Feisty, but now that Windows is gone well, is impossible :(. Anyway I will wait if The developers bring some light on this issue ^^

---

### Post by evil baz on 2007-05-25
OK news about this issue, After trying everything I got desperate and this is what I do:

I rebooted my pc, when I rebooted, I notice that the pc detects the HDD, so I decided toconnect it from the begining of the boot (when the BIOS is loaded) and guess what it mount it, but If I unmount and try to re-mount it, Ubuntu put it as a device error. this could help I will try to keep up in this wayy, until further notice about this "bug".

anyway someone know who reestablish USB 2.0 (because i downgrade to 1.1).

Thanks in advance.

---

