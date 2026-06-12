---
title: "Help getting lirc to work"
date: 2007-06-27
forum: General Help
---

### Post by andyrobo60 on 2007-06-27
I am trying to get lirc to work on xubuntu Feisty, I have followed about 5 different guides trying to get it to work with no luck. I have a Hauppauge PVR-150 with the USB IR receiver and blaster (I am NOT using the blaster).

When I run irw it exits and stops lirc running. 

When I do "dmesg | grep lirc" it gives me

```

[   52.430541] lirc_dev: IR Remote Control driver registered, at major 61 
[   52.450165] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.
[   52.453130] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.29 $
[   52.453135] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   52.456292] usbcore: registered new interface driver lirc_mceusb2

```

any help someone can give me would be very appreciated.

---

