---
title: "When I run 'insmod ./ch431.ko ' ,got unknow symbol error ..."
date: 2008-02-09
forum: General Help
---

### Post by qdzheng on 2008-02-09
Hello everyone.
I have a USB to Serial adapter&#65292;the chip is ch341.
I complier module myself(thanks  Frank A Kingswood <frank@kingswood-consulting.co.uk>) and all is ok before yesterday.

but,today when I run 'sudo insmod ./ch341.ko',system report:
   insmod: error inserting './ch341.ko': -1 Unknown symbol in module

someone told me: compile your module again when kernel is updated,I remember kernel is updated recently(from 2.6.22-14.49 to 2.6.22.14.51?). so,I compile ch341 module,and run insmod, I got that error again.

My image and header packages:

ii  linux-headers-2.6.22-14-generic            2.6.22-14.51                              
ii  linux-image-2.6.22-14-generic              2.6.22-14.51 

logs:

[63402.980000] ch341: Unknown symbol usb_serial_disconnect
[63402.980000] ch341: Unknown symbol usb_serial_generic_open
[63402.980000] ch341: Unknown symbol usb_serial_probe
[63402.980000] ch341: Unknown symbol usb_serial_register
[63402.980000] ch341: Unknown symbol usb_serial_deregister
[65110.352000] ch341: Unknown symbol usb_serial_disconnect
[65110.352000] ch341: Unknown symbol usb_serial_generic_open
[65110.352000] ch341: Unknown symbol usb_serial_probe
[65110.352000] ch341: Unknown symbol usb_serial_register
[65110.356000] ch341: Unknown symbol usb_serial_deregister


anyone can help me?  thanks.

---

### Post by kizmat on 2008-02-14
see [http://ohioloco.ubuntuforums.org/showpost.php?p=4334062&postcount=12](http://ohioloco.ubuntuforums.org/showpost.php?p=4334062&postcount=12)

you need to load usbserial first
* modprobe usbserial && insmod ch341.ko

---

