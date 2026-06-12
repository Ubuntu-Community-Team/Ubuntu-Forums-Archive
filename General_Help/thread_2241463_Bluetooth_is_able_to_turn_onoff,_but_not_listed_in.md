---
title: "Bluetooth is able to turn on/off, but not listed in lspci. Eh?"
date: 2014-08-26
forum: General Help
---

### Post by Roasted on 2014-08-26
Hello friends. Ubuntu 14.04.1, Dell Latitude E7440 (came with Ubuntu 12.04, swapped SSD with 14.04 from another Dell to this Dell). 

I have all of the latest updates, etc etc, but I'm not having any success with bluetooth. I became curious about using bluetooth (something that hasn't happened since forever since I never found bluetooth to be that useful), but I found that LibreOffice Impress has an Android remote app that can work over wifi and bluetooth. When running over wifi, it's great, but this got me curious about using bluetooth in case I'm ever in a non-wifi zone. Sure enough, I cannot get bluetooth to work.

What I'm finding is that I can enable/disable bluetooth without error via the indicator in the upper right. I can toggle visibility as well, and never receive an error. (I would think it would error out if it didn't find any bluetooth devices to use...?) The catch is, it just flat out will not pair. My phone will pair with other devices without issue, but I cannot see my laptop nor can my laptop see other bluetooth devices. It's just a continual circular spin as it keeps attempting, but never goes anywhere. 

Here's my dmesg and lspci. Not really sure what else to do from here. Any insight?

[http://paste.ubuntu.com/8150337/](http://paste.ubuntu.com/8150337/)

EDIT - For what it's worth, it's enabled in BIOS.

---

### Post by varunendra on 2014-08-27
Bluetooth is located over usb bus, not pci (even if it is integrated with the PCI wireless card). So it will show up in 'lsusb' and 'usb-devices'.

No idea about why it is not connecting though. I suggest installing blueman and check/change settings from its gui. It provides more control options than the default bluetooth manager of Ubuntu.

---

### Post by Roasted on 2014-08-27
Blueman provided me with nothing additional. Searching around still yielded nothing in the area, despite my phone broadcasting Bluetooth visibility.

Here's my lsusb and usb-devices in case anybody notices anything out of the ordinary.

[http://paste.ubuntu.com/8160118/](http://paste.ubuntu.com/8160118/)

---

### Post by rob_williams2 on 2015-04-22
Anyone find a solution to bluetooth on Dell e7440?

---

