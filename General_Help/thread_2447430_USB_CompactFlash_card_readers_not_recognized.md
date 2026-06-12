---
title: "USB CompactFlash card readers not recognized"
date: 2020-07-18
forum: General Help
---

### Post by peyre on 2020-07-18
I have an old camera that uses CompactFlash cards; I know it's old, but it still works well for what I need it for.  The trouble is that my new desktop doesn't have a CF reader built-in, so I've rummaged through to find my old external readers.  One is a Microtech ZiO! CF reader; the other is an SIIG Digital Media Express US2227 (it's a PC Card reader with a CF-PCCard adapter).  Neither seems to be recognized.  lsusb shows the SIIG device as 
```
Bus 003 Device 016: ID 07cc:0004 Carry Computer Eng., Co., Ltd SM/CF/PCMCIA Card Reader
```
but the ZiO doesn't seem to show in lsusb at all (too bad, it's the nicer reader).

Any suggestions anyone?

---

### Post by peyre on 2020-07-26
Bump?

---

### Post by kurt18947 on 2020-07-26
Sorry this isn't much help for your existing readers. I've installed a few multiple card readers in 3.5" floppy bays. They're typically USB connected and show up as boot devices in UEFI. I don't have any Compact Flash cards to see if they'll actually read. The only slot I usually use is the SD card reader and that works as expected.

---

### Post by peyre on 2020-07-28
Thanks for replying, at least.  I was feeling lonely, not having heard from anyone! ;)

Yes, I've used multi-card readers in *buntu, but not these old dedicated readers.  Too bad, really - I'd hate to buy something new when I have old gear that should do the trick just fine.

---

### Post by ActionParsnip on 2020-07-28
Boot with the device disconnected but without the storage inserted. Log in connect the device and run:
```

dmesg | tail

```
Insert the storage media, wait a few seconds then, again, run:
```
 
dmesg | tail

```
Paste the output as an update. It may help

---

### Post by Dennis N on 2020-07-28
I have SanDisk ImageMate CF, Model Number SDDR-91 and it works in Ubuntu 20.04. I would use that.
Since you are in California, you could get a new one for less than $20 on ebay. A used one for even less.

---

### Post by peyre on 2020-07-28
**ZiO card reader**

The connected but card not plugged in:
[ 5622.847367] usb usb3-port7: attempt power cycle
[ 5623.499380] usb 3-7: new full-speed USB device number 13 using xhci_hcd
[ 5623.499595] usb 3-7: Device not responding to setup address.
[ 5623.707535] usb 3-7: Device not responding to setup address.
[ 5623.915367] usb 3-7: device not accepting address 13, error -71
[ 5624.043339] usb 3-7: new full-speed USB device number 14 using xhci_hcd
[ 5624.043501] usb 3-7: Device not responding to setup address.
[ 5624.251549] usb 3-7: Device not responding to setup address.
[ 5624.459282] usb 3-7: device not accepting address 14, error -71
[ 5624.459367] usb usb3-port7: unable to enumerate USB device

With a CF card plugged in:
[ 5622.847367] usb usb3-port7: attempt power cycle
[ 5623.499380] usb 3-7: new full-speed USB device number 13 using xhci_hcd
[ 5623.499595] usb 3-7: Device not responding to setup address.
[ 5623.707535] usb 3-7: Device not responding to setup address.
[ 5623.915367] usb 3-7: device not accepting address 13, error -71
[ 5624.043339] usb 3-7: new full-speed USB device number 14 using xhci_hcd
[ 5624.043501] usb 3-7: Device not responding to setup address.
[ 5624.251549] usb 3-7: Device not responding to setup address.
[ 5624.459282] usb 3-7: device not accepting address 14, error -71
[ 5624.459367] usb usb3-port7: unable to enumerate USB device

**SIIG reader:**

Plugged in, no CF card:
[ 5623.707535] usb 3-7: Device not responding to setup address.
[ 5623.915367] usb 3-7: device not accepting address 13, error -71
[ 5624.043339] usb 3-7: new full-speed USB device number 14 using xhci_hcd
[ 5624.043501] usb 3-7: Device not responding to setup address.
[ 5624.251549] usb 3-7: Device not responding to setup address.
[ 5624.459282] usb 3-7: device not accepting address 14, error -71
[ 5624.459367] usb usb3-port7: unable to enumerate USB device
[ 5759.982792] usb 3-8: new full-speed USB device number 15 using xhci_hcd
[ 5760.131439] usb 3-8: New USB device found, idVendor=07cc, idProduct=0004, bcdDevice= 0.01
[ 5760.131445] usb 3-8: New USB device strings: Mfr=0, Product=0, SerialNumber=0

CF Card plugged in:
[ 5623.707535] usb 3-7: Device not responding to setup address.
[ 5623.915367] usb 3-7: device not accepting address 13, error -71
[ 5624.043339] usb 3-7: new full-speed USB device number 14 using xhci_hcd
[ 5624.043501] usb 3-7: Device not responding to setup address.
[ 5624.251549] usb 3-7: Device not responding to setup address.
[ 5624.459282] usb 3-7: device not accepting address 14, error -71
[ 5624.459367] usb usb3-port7: unable to enumerate USB device
[ 5759.982792] usb 3-8: new full-speed USB device number 15 using xhci_hcd
[ 5760.131439] usb 3-8: New USB device found, idVendor=07cc, idProduct=0004, bcdDevice= 0.01
[ 5760.131445] usb 3-8: New USB device strings: Mfr=0, Product=0, SerialNumber=0

---

### Post by peyre on 2020-07-29
Looks like there was no change!  I've brought them into the office to try them on a different Xubuntu machine, and with a different CF card.

**ZiO**
No CF card:
[ 2493.281916] usb usb3-port6: attempt power cycle
[ 2493.933726] usb 3-6: new full-speed USB device number 9 using xhci_hcd
[ 2493.933884] usb 3-6: Device not responding to setup address.
[ 2494.142005] usb 3-6: Device not responding to setup address.
[ 2494.349730] usb 3-6: device not accepting address 9, error -71
[ 2494.477743] usb 3-6: new full-speed USB device number 10 using xhci_hcd
[ 2494.477929] usb 3-6: Device not responding to setup address.
[ 2494.685986] usb 3-6: Device not responding to setup address.
[ 2494.893836] usb 3-6: device not accepting address 10, error -71
[ 2494.893953] usb usb3-port6: unable to enumerate USB device

With CF Card:
[ 2493.281916] usb usb3-port6: attempt power cycle
[ 2493.933726] usb 3-6: new full-speed USB device number 9 using xhci_hcd
[ 2493.933884] usb 3-6: Device not responding to setup address.
[ 2494.142005] usb 3-6: Device not responding to setup address.
[ 2494.349730] usb 3-6: device not accepting address 9, error -71
[ 2494.477743] usb 3-6: new full-speed USB device number 10 using xhci_hcd
[ 2494.477929] usb 3-6: Device not responding to setup address.
[ 2494.685986] usb 3-6: Device not responding to setup address.
[ 2494.893836] usb 3-6: device not accepting address 10, error -71
[ 2494.893953] usb usb3-port6: unable to enumerate USB device

**SIIG:**
[ 2494.142005] usb 3-6: Device not responding to setup address.
[ 2494.349730] usb 3-6: device not accepting address 9, error -71
[ 2494.477743] usb 3-6: new full-speed USB device number 10 using xhci_hcd
[ 2494.477929] usb 3-6: Device not responding to setup address.
[ 2494.685986] usb 3-6: Device not responding to setup address.
[ 2494.893836] usb 3-6: device not accepting address 10, error -71
[ 2494.893953] usb usb3-port6: unable to enumerate USB device
[ 2701.899642] usb 3-6: new full-speed USB device number 11 using xhci_hcd
[ 2702.048298] usb 3-6: New USB device found, idVendor=07cc, idProduct=0004, bcdDevice= 0.01
[ 2702.048314] usb 3-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0

With CF Card:
[ 2494.142005] usb 3-6: Device not responding to setup address.
[ 2494.349730] usb 3-6: device not accepting address 9, error -71
[ 2494.477743] usb 3-6: new full-speed USB device number 10 using xhci_hcd
[ 2494.477929] usb 3-6: Device not responding to setup address.
[ 2494.685986] usb 3-6: Device not responding to setup address.
[ 2494.893836] usb 3-6: device not accepting address 10, error -71
[ 2494.893953] usb usb3-port6: unable to enumerate USB device
[ 2701.899642] usb 3-6: new full-speed USB device number 11 using xhci_hcd
[ 2702.048298] usb 3-6: New USB device found, idVendor=07cc, idProduct=0004, bcdDevice= 0.01
[ 2702.048314] usb 3-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0

---

### Post by peyre on 2020-07-29
So, still the same!  I'm surprised that the system completely fails to recognize either.  It's not like this is LPT technology or something.

Thanks Dennis.  You're probably right; I just hate to buy something new when I have two older card readers specifically designed for the kind of card I need to read.

---

### Post by peyre on 2020-12-09
Update: I just tried the ZiO! device on a Win10 machine, and Device Manager says 
> Windows has stopped this device because it has reported problems. (Code 43)
A request for the USB device descriptor failed.

And when I try to run the Setup.exe from the driver disk, it says "This app can't run on your PC", so maybe these devices are just incompatible with 64-bit operating systems.

---

