---
title: "[SOLVED] Identifying how Ubuntu Names a Device"
date: 2008-05-15
forum: General Help
---

### Post by Alien.col on 2008-05-15
Hello: 

I'm trying to configure my FM tuner card and a gnomeradio is asking me to name the device, the default is "/dev/radio" but it says it can't find it in that address. The thing is I don't know it either! I tried lshw in console and this is the output of the device. How can I find out that address.

lshw output:

*-multimedia
             description: Multimedia controller
             product: SAA7133/SAA7135 Video Broadcast Decoder
             vendor: Philips Semiconductors
             physical id: 7
             bus info: pci@0000:01:07.0
             version: d1
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=saa7134 latency=32 maxlatency=40 mingnt=16 module=saa7134

---

### Post by Alien.col on 2008-05-16
bump

---

### Post by Ayuthia on 2008-05-16
You might be able to find the device by looking through lshal in the Terminal:
```
lshal|less
```
It lists the device location for some of the hardware.  Not for sure if it will help you or not.

---

### Post by Alien.col on 2008-05-16
Well it did help i got this from the device i wanted, but i don't know if the address is the info.parent or the udi:

lshal --show pci_1131_7133
udi = '/org/freedesktop/Hal/devices/pci_1131_7133'
  info.linux.driver = 'saa7134'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_5c'  (string)
  info.product = 'SAA7133/SAA7135 Video Broadcast Decoder'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1131_7133'  (string)
  info.vendor = 'Philips Semiconductors'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0/0000:01:07.0'  (string)
  pci.device_class = 4  (0x4)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0/0000:01:07.0'  (string)
  pci.product = 'SAA7133/SAA7135 Video Broadcast Decoder'  (string)
  pci.product_id = 28979  (0x7133)  (int)
  pci.subsys_product_id = 28982  (0x7136)  (int)
  pci.subsys_vendor = 'KWorld Computer Co. Ltd.'  (string)
  pci.subsys_vendor_id = 6110  (0x17de)  (int)
  pci.vendor = 'Philips Semiconductors'  (string)
  pci.vendor_id = 4401  (0x1131)  (int)


Thanks a lot dud you rule.

---

### Post by Alien.col on 2008-05-16
I' not really sure those addresses are it, i was expecting something like "dev/video1" or something similar.

---

### Post by psavva on 2008-05-16
I've also had this poblem in the past.

Open Terminal

> ls /dev/radio*

That should tell you which is your radio device.

Just for the record, mine was /dev/radio0

Good Luck :D

---

### Post by Alien.col on 2008-05-16
Thanks dude, found it, it finally was not listed as a radio device but as a video device.

[php]
ls /dev/video* 
/dev/video0
[/php]

---

