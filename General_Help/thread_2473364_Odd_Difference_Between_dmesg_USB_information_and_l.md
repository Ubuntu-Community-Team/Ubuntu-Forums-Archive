---
title: "Odd Difference Between dmesg USB information and lsusb information?"
date: 2022-04-02
forum: General Help
---

### Post by jibunnokage on 2022-04-02
Ok, never seen this one before, after years of using Debian, Pi OS, etc.  Now using Ubuntu LTS, and I notice the following device and seeking insight of how or why this might be happening?

I inserted a USB device, in this case a fingerprint reader.  And dmesg shows the device, and expect UDEV handled accordingly.  But when I use lsusb, I don't see the device at all.

```

# dmesg
[ 3483.867480] usb 2-2.2: USB disconnect, device number 5
[ 3489.479107] usb 2-2.2: new full-speed USB device number 6 using uhci_hcd
[ 3489.787683] usb 2-2.2: New USB device found, idVendor=2f0a, idProduct=0201, bcdDevice= 0.01
[ 3489.787692] usb 2-2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 3489.787695] usb 2-2.2: Product: Security Caliburn by Pixelauth
[ 3489.787698] usb 2-2.2: Manufacturer: Pixelauth

# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 006: ID 2f0a:0201 VMware, Inc. VMware Virtual USB Hub
Bus 002 Device 004: ID 0e0f:0008 VMware, Inc. VMware Virtual USB Mouse
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Any suggestions on where or what logs or such I should look at to try to figure out what is going on here?  Running this in a VMware VM, but still the VM sees the USB device at the virtual hardware level just fine.  Otherwise dmesg would be blind to the insert of the device, right?

-JnK

---

### Post by Holger_Gehrke on 2022-04-02
Fingerprint readers are a bit of a special case. Because of their rather doubtful security a lot of manufacturers try to add "security by obscurity" to their product which makes it very difficult to write device drivers for them. If you try a web search for"Security Caliburn" and "Pixelauth" you'll get lots and lots of completely unrelated hits (my favourite of those : "No Security Jobs in Caliburn") and a few hits with posts by people looking for drivers for this device. The identification you see in the dmesg output is provided by the device. If you look at the lsusb output you'll see in the ID field for Bus 002 Device 006 that the device ends up getting seen as a VMware Virtual USB Hub. If you have a guest OS which has drivers for this device (probably Windows ...) than it will work in the guest, otherwise it won't.

Holger

---

### Post by jibunnokage on 2022-04-02
Yeah, all true... already saw the 'No security jobs in Caliburn' as well, had to laugh.

---

