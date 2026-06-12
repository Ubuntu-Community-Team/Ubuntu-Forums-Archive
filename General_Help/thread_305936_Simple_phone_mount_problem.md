---
title: "Simple phone mount problem?"
date: 2006-11-24
forum: General Help
---

### Post by FurryNemesis on 2006-11-24
I'm trying to get my Nokia N70 mounted via usb, to browse and transfer files (mostly photos/videos). I've tried various bluetooth solutions plus kmobiletools and gnokii (which didn't work) on the forums but don't really need that kind of functionality.

Anyway, Device Manager sees the phone:

[IMG]http://img.photobucket.com/albums/v155/openspy/Screenshot-DeviceManager.png[/IMG]

and dmesg spits this out:

[17186230.472000] cdc_acm 3-1:1.8: ttyACM0: USB ACM device
[17186230.476000] usbcore: registered new driver cdc_acm
[17186230.476000] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapters
[17186501.852000] usb 3-1: USB disconnect, address 2
[17186506.944000] usb 3-1: new full speed USB device using ohci_hcd and address 3
[17186507.176000] cdc_acm 3-1:1.8: ttyACM0: USB ACM device

...which confirms that, yep, it saw the usb connection. 

Now, do I need a certain mount command (obexserver already installed) or do I edit fstab.conf first?

Thanks in advance.

---

### Post by FurryNemesis on 2006-12-01
Fixed via kde-bluetooth-framework :D

---

### Post by cvmostert on 2006-12-13
Please let us know what you did to get file transfer working on your n70. there are a few people who would gain alot by your info... me included.

I can send and receive files via bluetooth, but not USB

---

