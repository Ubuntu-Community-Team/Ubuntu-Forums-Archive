---
title: "USB devices do not Automount on Dell GX240"
date: 2007-08-22
forum: General Help
---

### Post by dcoffey48 on 2007-08-22
I have tried 2 different usb thumb drives and 1 ipod on  2 different Dell Optiplex gx240's running ubuntu 7.04  Neither will  automount either device.  Here is the dmesg output after connecting my ipod. 

1081.046365] usb 2-2: new full speed USB device using uhci_hcd and address 2
[ 1084.841863] usb 2-2: configuration #1 chosen from 2 choices
[ 1085.197916] usbcore: registered new interface driver libusual
[ 1085.218276] Initializing USB Mass Storage driver...
[ 1085.218424] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1085.218530] usbcore: registered new interface driver usb-storage
[ 1085.218537] USB Mass Storage support registered.
[ 1085.218783] usb-storage: device found at 2
[ 1085.218787] usb-storage: waiting for device to settle before scanning
[ 1090.385966] usb-storage: device scan complete
[ 1091.140823] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 1092.400638] SCSI device sdb: 14651280 2048-byte hdwr sectors (30006 MB)

I think the problem is that Ubuntu thinks that my usb controler is usb 2 but I dont think it is.  I have already tried:

sudo rmmod ehci_hcd

With the following result:

ERROR: Module ehci_hcd does not exist in /proc/modules

I have successfully mounted Both the thumb drive and the ipod on different computer running Ubuntu 7.04.

Any help is apreciated.

Dave.

---

### Post by strider_mt2k on 2007-08-24
I can't be of much help other than to say that the front ports on the GX240 don't work for folks "out of the box" and that the USB is indeed USB 1.

If you've gotten your front ports to work I'd love to hear how because it's the only flaw I've found so far with my Feisty install.

---

### Post by dcoffey48 on 2007-08-24
I tried the usb ports on the back and they work fine.

I had not thought about trying the ports on the back.  I figured they were the same.  But apparently not.

Thanks,
Dave.

---

### Post by samichx on 2007-11-06
bump,

---

