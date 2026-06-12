---
title: "Question not only about Ubuntu. again mp3 player"
date: 2008-02-21
forum: General Help
---

### Post by royksol on 2008-02-21
mp3 player was used under Windows. Once PC didn't recognize it. Player is working, it can be charged from USB, but still PC doesn't see it. 
I have tried many times on different machines. In player options choosed *UMS only*. So it should be seen as Storage Device. In player options there is one difference: *System Info-> Version* menu is showing system error. I suppose it means, that something wrong is with firmware. 
On official Samsung webpage firmware updates can be found(*.dat binary file). 
But how to make update without connection to PC? impossible.
What is the root of all this trouble?
Software(player firmware), hardware, cable? And is there any way to mount it on such flexible OS as Linux :) (P.S. I had flash drive, which isn't working in Windows, but in Ubuntu every time I mount it and use like a charm) 

Some technical info. **dmesg |grep usb **is absolute same before and after pluging player in(but maybe it's history from yesterday ;) ). 
```
[   32.569610] usbcore: registered new driver usbfs
[   32.569635] usbcore: registered new driver hub
[   32.579986] usb usb1: configuration #1 chosen from 1 choice
[   32.684544] usb usb2: configuration #1 chosen from 1 choice
[   32.792421] usb usb3: configuration #1 chosen from 1 choice
[   32.896414] usb usb4: configuration #1 chosen from 1 choice
[   33.000826] usb usb5: configuration #1 chosen from 1 choice
[   34.144140] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   35.028141] usb 3-1: device descriptor read/all, error -84
[   35.907941] usb 3-1: new low speed USB device using uhci_hcd and address 4
[   36.791931] usb 3-1: device descriptor read/all, error -84
[   37.671757] usb 3-1: new low speed USB device using uhci_hcd and address 6
[   38.555731] usb 3-1: device descriptor read/all, error -84
[   39.435588] usb 3-1: new low speed USB device using uhci_hcd and address 8
[   41.199433] usb 3-1: new low speed USB device using uhci_hcd and address 9
[   43.215195] usb 3-1: new low speed USB device using uhci_hcd and address 10
[   43.381221] usb 3-1: configuration #1 chosen from 1 choice
[   43.441492] usbcore: registered new driver hiddev
[   43.457242] input: USB HID v1.10 Keyboard [HID 04f3:0103] on usb-0000:00:10.2-1
[   43.483233] input: USB HID v1.10 Device [HID 04f3:0103] on usb-0000:00:10.2-1
[   43.483243] usbcore: registered new driver usbhid
[   43.483246] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

```
Only keyboard and player is pluged.

Player is Samsung YP-Z5F with 2 Gb. There is no warranty thats why any method or advise is pleased.

---

