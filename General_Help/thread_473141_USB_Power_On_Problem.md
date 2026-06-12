---
title: "USB Power On Problem"
date: 2007-06-13
forum: General Help
---

### Post by ==[ VNMS1 ]== on 2007-06-13
I'm having some trouble with my "el cheapo" 4 port USB hub. It works when I plug it in while the computer is already on, however I cannot leave it plugged in while I power up. If It is plugged in when I turn the computer on, the system stops before the POST...is this a BIOS problem or something else? The device is 2.0 compliant with backward compatability to 1.2 and I'm plugging it into a P3 Compaq Deskpro EN (Old I know, but it works) with Feisty Fawn. here is the readout for dmesg | tail

~$ dmesg | tail
[   66.657068] Bluetooth: L2CAP ver 2.8
[   66.657083] Bluetooth: L2CAP socket layer initialized
[   66.682115] Bluetooth: RFCOMM socket layer initialized
[   66.682157] Bluetooth: RFCOMM TTY layer initialized
[   66.682163] Bluetooth: RFCOMM ver 1.8
[   75.052317] eth0: no IPv6 routers present
[   99.265050] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   99.419578] usb 1-2: configuration #1 chosen from 1 choice
[   99.422523] hub 1-2:1.0: USB hub found
[   99.425400] hub 1-2:1.0: 4 ports detected

So the hub is detected in Ubuntu, but it seems to interfere with the POST. Can anyone fathom a guess as to how I can solve this? I can unplug it everytime power on, but the USB ports are at the back and this is a very annoying process to go through.

Any help anyone? Please.

---

