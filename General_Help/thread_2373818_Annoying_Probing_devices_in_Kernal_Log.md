---
title: "Annoying Probing devices in Kernal Log"
date: 2017-10-10
forum: General Help
---

### Post by jim38 on 2017-10-10
Hello Was wondering if I could get some help with the device driver annoying  probing . Its called "really probing"  I think it is caused from '/drivers/base/dd,c'
I would like to not see this in my kernel log when loading USB and PCI drivers for DTV  Does anyone know why I see this on one kernel but, not another kernal "same machine"
Is there somrthing I need to install or add to my .conf

Here's a small snippet of the log  probing and all the PM: stuff. I could post the whole thing if needed. it gets longer :)

kernel  4.3.6+ USB device 'Genpix 8PSK-to-USB2 

```
 1415.529707] usb 1-1.2: new high-speed USB device number 4 using ehci-pci
 [ 1415.615035] usb 1-1.2: New USB device found, idVendor=09c0, idProduct=0200
 [ 1415.615041] usb 1-1.2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
 [ 1415.615044] device: '1-1.2': device_add
 [ 1415.615080] bus: 'usb': add device 1-1.2
 [ 1415.615095] PM: Adding info for usb:1-1.2
[ 1415.667310]  bus: 'usb': driver_probe_device: matched device 1-1.2 with driver usb
 [ 1415.615211] bus: 'usb': really_probe: probing driver usb with device 1-1.2
 [ 1415.615218] devices_kset: Moving 1-1.2 to end of list
 [ 1415.615544] device: '1-1.2:1.0': device_add
 [ 1415.615563] bus: 'usb': add device 1-1.2:1.0
 [ 1415.615569] PM: Adding info for usb:1-1.2:1.0
  [ 1415.667313]driver: 'usb': driver_bound: bound to device '1-1.2'
[ 1415.615612] bus: 'usb': really_probe: bound device 1-1.2 to driver usb
 [ 1415.615642] device: 'ep_00': device_add
 [ 1415.615664] PM: Adding info for No Bus:ep_00
 [ 1415.662262] device class 'rc': registering
 [ 1415.667290] bus: 'usb': add driver dvb_usb_gp8psk
 [ 1415.667302] bus: 'usb': driver_probe_device: matched device 1-1.2:1.0 with driver dvb_usb_gp8psk
 [ 1415.667305] bus: 'usb': really_probe: probing driver dvb_usb_gp8psk with device 1-1.2:1.0
 [ 1415.667310] devices_kset: Moving 1-1.2:1.0 to end of list
[ 1415.667313] dvb-usb: found a 'Genpix 8PSK-to-USB2 Rev.1 DVB-S receiver' in cold state, will try to load a firmware
 [ 1415.667317] __allocate_fw_buf: fw-dvb-usb-gp8psk-01.fw buf=ffff8802015c5840


```

Then same machine different kernel  4.1.0-rc3+  Same USB device,,  As you can see  the same device below installs without all the probing, adding info, moviing to the end of list stuff.

```

Sep  5 20:55:15 jimiam kernel: [  197.803741] usb 3-1.2: new high-speed USB device number 4 using ehci-pci
Sep  5 20:55:15 jimiam kernel: [  197.896098] usb 3-1.2: New USB device found, idVendor=09c0, idProduct=0200
Sep  5 20:55:15 jimiam kernel: [  197.896104] usb 3-1.2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Sep  5 20:55:15 jimiam kernel: [  197.979661] dvb-usb: found a 'Genpix 8PSK-to-USB2 Rev.1 DVB-S receiver' in cold state, will try to load a firmware
Sep  5 20:55:15 jimiam kernel: [  197.992195] dvb-usb: downloading firmware from file 'dvb-usb-gp8psk-01.fw'
Sep  5 20:55:15 jimiam kernel: [  198.067178] gp8psk: found Genpix USB device pID = 200 (hex)
Sep  5 20:55:15 jimiam kernel: [  198.067224] usbcore: registered new interface driver dvb_usb_gp8psk
Sep  5 20:55:15 jimiam kernel: [  198.119288] usb 3-1.2: USB disconnect, device number 4
Sep  5 20:55:15 jimiam kernel: [  198.119329] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
Sep  5 20:55:17 jimiam kernel: [  199.850414] usb 3-1.2: new high-speed USB device number 5 using ehci-pci
Sep  5 20:55:17 jimiam kernel: [  199.943034] usb 3-1.2: New USB device found, idVendor=09c0, idProduct=0201
Sep  5 20:55:17 jimiam kernel: [  199.943038] usb 3-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep  5 20:55:17 jimiam kernel: [  199.943039] usb 3-1.2: Product: 8PSK to USB 2.0 adapter
Sep  5 20:55:17 jimiam kernel: [  199.943041] usb 3-1.2: Manufacturer: Genpix Electronics
Sep  5 20:55:17 jimiam kernel: [  199.943042] usb 3-1.2: SerialNumber: 00143
Sep  5 20:55:17 jimiam kernel: [  199.943276] dvb-usb: found a 'Genpix 8PSK-to-USB2 Rev.1 DVB-S receiver' in warm state.
Sep  5 20:55:17 jimiam kernel: [  200.348621] gp8psk: FW Version = 2.02.4 (0x20204)  Build 2007/01/16
Sep  5 20:55:17 jimiam kernel: [  200.348741] gp8psk: FPGA Version = 2
Sep  5 20:55:17 jimiam kernel: [  200.365583] gp8psk: downloading bcm4500 firmware from file 'dvb-usb-gp8psk-02.fw'
Sep  5 20:55:17 jimiam kernel: [  200.763592] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Sep  5 20:55:17 jimiam kernel: [  200.763851] DVB: registering new adapter (Genpix 8PSK-to-USB2 Rev.1 DVB-S receiver)
Sep  5 20:55:17 jimiam kernel: [  200.797659] gp8psk_fe: Frontend revision 1 attached
Sep  5 20:55:17 jimiam kernel: [  200.797669] usb 3-1.2: DVB: registering adapter 1 frontend 0 (Genpix DVB-S)...
Sep  5 20:55:17 jimiam kernel: [  200.798244] dvb-usb: Genpix 8PSK-to-USB2 Rev.1 DVB-S receiver successfully initialized and connected.
Sep  5 20:55:17 jimiam kernel: [  200.798247] gp8psk: found Genpix USB device pID = 201 (hex)

```

Thanks for Looking

---

### Post by jim38 on 2017-10-10
[SIZE=2]

Examples of a weird driver probing in kernlog. Reason I don't like this is, I'm worried some devices may not get installed correctly and I want to be sure. What is this??

 [ 1415.615612] [COLOR=#0000cd]bus: 'usb': really_probe:[/COLOR] bound device 1-1.2 to driver usb
 [ 1415.615642] device: 'ep_00': device_add
 [ 1415.615664] [COLOR=#0000cd]PM: Adding info for No Bus[/COLOR]:ep_00
 [ 1415.662262] device class 'rc': registering
 [ 1415.667290] bus: 'usb': add driver dvb_usb_gp8psk

[/SIZE][B][ 1415.667302] bus: 'usb': driver_probe_device: matched device 1-1.2:1.0 with driver dvb_usb_gp8psk
[ 1415.667305] bus: 'usb': [COLOR=#0000cd]really_probe: probing driver[/COLOR] dvb_usb_gp8psk with device 1-1.2:1.0

[ 1415.667310] devices_kset: [COLOR=#0000cd]Moving 1-1.2:1.0 to end of list[/COLOR][/B]

---

