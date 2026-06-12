---
title: "[SOLVED] xubuntu 7.04 really slow usb"
date: 2007-09-16
forum: General Help
---

### Post by tlacuache on 2007-09-16
I've got kind of a weird problem... I picked up a little "shuttle" micro atx computer to sit next to my TV so I can watch videos I download via bittorrent. It's not the beefiest box, so I put Xubuntu 7.04 on there. Got everything set up and working like a charm.

Except...

I noticed that USB transfers are painfully slow. When I plug in my thumb drive, dmesg reports that it sees a "full speed" USB device. However, in /proc/bus/usb/devices I see it's only running at 12 Mb/s (should be something like 480, shouldn't it?).

Odd thing is, I plug the exact same device into my desktop (also running 7.04) and it's reported as a "high speed" device and proc shows it's running at the correct, faster speed.

One thing I did notice was that when I "ls mod |grep usb" and in dmesg on the shuttle, I see "uhci_hcd" is what's handling the USB. On my desktop, I see ohci_hcd,ehci_hcd instead. I tried to rmmod uhci_hcd and modprobe the other two, but after I do that nothing shows up in dmesg when I plug the drive in.

Any help would be appreciated.

Thanks,

Seth Grover

---

### Post by Delkster on 2007-09-16
> **tlacuache said:**
> I noticed that USB transfers are painfully slow. When I plug in my thumb drive, dmesg reports that it sees a "full speed" USB device. However, in /proc/bus/usb/devices I see it's only running at 12 Mb/s (should be something like 480, shouldn't it?).
"Full speed" refers to the full speed of the USB 1.x specification which *is* 12 Mbps. 480 Mbps on USB 2.x is usually called "high speed" or something.

> Odd thing is, I plug the exact same device into my desktop (also running 7.04) and it's reported as a "high speed" device and proc shows it's running at the correct, faster speed.

One thing I did notice was that when I "ls mod |grep usb" and in dmesg on the shuttle, I see "uhci_hcd" is what's handling the USB. On my desktop, I see ohci_hcd,ehci_hcd instead.
OHCI and UHCI are USB 1.x level USB controllers. EHCI would be 2.x. Either the Shuttle box doesn't have USB 2.x support or Ubuntu doesn't detect its USB 2.x controller for some reason. Further specifications of the machine would help in figuring out which one it is, but unless you know for certain that the computer does have a USB 2.x controller, my guess is that it doesn't.

Try entering "lspci" in the terminal and post the results -- that might tell us something. Also, if you know the motherboard chipset, that'd help a lot.

---

### Post by tlacuache on 2007-09-16
Hey, I did the lspci thing like you said and yup, the controller is only USB 1.1. So... I dug around a box of PCI cards I had and found a USB 2.0 controller in there. I installed it and fired it up, and it uses 2.0, so that's good enough for me. I guess I'll use the onboard usb for keyboard and mouse and whatnot and the ports on the high speed card for storage devices.

Thanks.

---

