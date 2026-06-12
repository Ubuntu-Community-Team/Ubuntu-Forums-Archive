---
title: "Jabra BT620s"
date: 2008-04-05
forum: General Help
---

### Post by bogdan_5844 on 2008-04-05
So,I have the bt620s,usb headset.

In vista,i connected them and it automatically made them the default audio device.

In ubuntu,i looked and found out that on the Sound panel i should have the option to select USB Device,wich i don't.

This is the output of dmesg|tail:

```
[  310.852000] input: Jabra BT620s as /class/input/input9
[  310.852000] input: USB HID v1.11 Device [Jabra BT620s] on usb-0000:00:0b.0-1
[  310.852000] usbcore: registered new interface driver xpad
[  310.852000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[  311.084000] 6:1:0 : no or invalid class specific endpoint descriptor
[  311.152000] usb 1-1: USB disconnect, address 6
[  311.160000] usbcore: registered new interface driver snd-usb-audio
[  312.832000] usb 1-1: new full speed USB device using ohci_hcd and address 7
[  313.792000] usb 1-1: new full speed USB device using ohci_hcd and address 8
[  314.060000] usb 1-1: configuration #1 chosen from 1 choice

```


lsusb detects them:

```
Bus 002 Device 002: ID 174f:a821
Bus 002 Device 001: ID 0000:0000  
**Bus 001 Device 009: ID 0b0e:620c GN Netcom** 
Bus 001 Device 003: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 001 Device 001: ID 0000:0000  
```

The first usb device is the laptop's integrated camera,the third (i suppose) are the jabras,and the fourth is the usb mouse i use.

Note: i want to use this headset as an usb device,not as a bluetooth one,as i don't have a bluetooth stick.

Please help,i am out of ideas :confused:

---

### Post by bogdan_5844 on 2008-04-13
No answer..?

---

### Post by bogdan_5844 on 2008-05-14
bump....

---

### Post by benklop on 2008-05-23
I have this same headset, and the same happens to me. It appears to be a quirky headset that the driver doesn't support yet.

I compiled the ALSA usb-audio driver from the most recent version, but it still doesn't work. I am going to try the GIT development version today. If that still doesn't work, i will start trying to fix it myself, and i will post a patch if i can make it work.

---

### Post by benklop on 2008-06-15
The GIT versions don't work either, and I have been too occupied with classes to really try to make a headset work. I might suggest the original poster buy a 6 dollar bluetooth stick, as these headphones really do work beautifully in that mode.

---

