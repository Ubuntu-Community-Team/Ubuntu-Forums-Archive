---
title: "Mount USB Drive from Command line"
date: 2007-04-06
forum: General Help
---

### Post by djseto on 2007-04-06
How do you mount a USB drive from a command line? I am completely new to linux...

---

### Post by strabes on 2007-04-06
First of all does it not mount automagically?

If not try this

sudo mkdir /media/USBSTICK && sudo mount /dev/sdb /media/USBSTICK

If that doesn't work try /dev/sdb1 instead of /dev/sdb

---

### Post by djseto on 2007-04-06
doesnt work. 

i tried sudo mkdir /media/USBSTICK && sudo mount /dev/sdb /media/USBSTICK

and it says I need to specify the file system type.

I dont get this mount thing at all and my GUI wont load after I did the get update. The whole reason I want to mount my USB drive is so I can re-install  a driver to fix it.

---

### Post by fdrake on 2007-04-06
try this :
sudo mount -t usbfs /dev/sdb /media/USBSTICK

---

### Post by dmizer on 2007-04-06
we need to figure out what your machine is labeling your usb stick.

after you connect your stick, post the output of:
```
dmesg | grep usb
```

---

### Post by djseto on 2007-04-06
[   22.748381] usbcore: registered new driver usbfs
[   22.748404] usbcore: registered new driver hub
[   22.829580] usb usb1: configuration #1 chosen from 1 choice
[   23.243268] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   23.462145] usb 1-1: configuration #1 chosen from 1 choice
[   23.767010] usb 1-6: new low speed USB device using ohci_hcd and address 3
[   23.981790] usb 1-6: configuration #1 chosen from 1 choice
[   23.984808] usbcore: registered new driver hiddev
[   23.986158] usb usb2: configuration #1 chosen from 1 choice
[   24.458669] usb 1-1: USB disconnect, address 2
[   24.458784] usbcore: registered new driver usbhid
[   24.458787] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   24.762508] usb 1-1: new low speed USB device using ohci_hcd and address 4
[   24.981128] usb 1-1: configuration #1 chosen from 1 choice
[   24.995135] input: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:0b.0-1
[   25.015151] input: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:0b.0-1
[   25.015201] usb 1-6: USB disconnect, address 3
[   25.318222] usb 1-6: new low speed USB device using ohci_hcd and address 5
[   25.532758] usb 1-6: configuration #1 chosen from 1 choice
[   25.545784] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:0b.0-6
[  261.556537] usb 2-5: new high speed USB device using ehci_hcd and address 4
[  261.689850] usb 2-5: configuration #1 chosen from 1 choice
[  261.723498] usbcore: registered new driver libusual
[  261.732830] usbcore: registered new driver usb-storage
[  261.732948] usb-storage: device found at 4
[  261.732950] usb-storage: waiting for device to settle before scanning
[  266.729967] usb-storage: device scan complete

---

### Post by dmizer on 2007-04-06
humm ... that didn't tell me what i wanted to know at all.

try doing a complete dmesg, and just post everything that comes after "usb 2-5: new high speed USB device using ehci_hcd and address 4"

---

### Post by djseto on 2007-04-06
32.975333] usb 2-5: new high speed USB device using ehci_hcd and address 3
[   33.116353] usb 2-5: configuration #1 chosen from 1 choice
[   33.117348] usb 1-1: USB disconnect, address 2
[   33.419128] usb 1-1: new low speed USB device using ohci_hcd and address 3
[   33.641756] usb 1-1: configuration #1 chosen from 1 choice
[   33.644813] usbcore: registered new driver libusual
[   33.648412] Initializing USB Mass Storage driver...
[   33.648467] scsi4 : SCSI emulation for USB Mass Storage devices
[   33.648518] usb-storage: device found at 3
[   33.648520] usb-storage: waiting for device to settle before scanning
[   33.648532] usbcore: registered new driver usb-storage
[   33.648534] USB Mass Storage support registered.
[   33.655622] usbcore: registered new driver hiddev
[   33.665840] input: Logitech Logitech USB Keyboard as /class/input/input1
[   33.665849] input: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:0b.0-1
[   33.685914] input: Logitech Logitech USB Keyboard as /class/input/input2
[   33.686101] input: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:0b.0-1
[   33.686111] usbcore: registered new driver usbhid
[   33.686114] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

thanks

---

### Post by dmizer on 2007-04-06
it's still not registering as a device.

let's try something else.  edit /etc/modprobe.d/blacklist like so:
```
gksudo gedit /etc/modprobe.d/blacklist
```
and put this line at the end of the file:
```
blacklist ohci_hcd
```
save the file, reboot (with your usb drive disconnected).  once you've completely logged in, connect  your usb drive and post the same output for dmesg as you did above.

---

### Post by djseto on 2007-04-08
I got GNOME to finally load correctly after doing a sudo apt-get install ubuntu-desktop. For whatever reason, the version on the CD didn't play nice. Thanks for all your help though

---

