---
title: "USB serial port adapter dificulty"
date: 2018-02-06
forum: General Help
---

### Post by mb195811 on 2018-02-06
I am new to linux and I get the following error when trying to communicate with a hand held radio.  
 
 
 Failed to communicate with radio: 'Serial' object has no attribute 'setTimeout'
 
 
  I have read the forums, learned 2 new commands (lsusb & dmesg) and was able to determine that the USB adapter cable is recognized and I was able to assign it to /dev/ttyUSB0.  Is there something else I need to configure?  Also, how do I edit the /etc/modules file to load configuration on boot.  It is read only.

 
 
 us 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
 Bus 002 Device 007: ID 1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter
 
 
 
 
 [14790.947949] usb 2-2: new full-speed USB device number 6 using ohci-pci
 [14791.169431] usb 2-2: New USB device found, idVendor=1a86, idProduct=7523
 [14791.169439] usb 2-2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
 [14791.169443] usb 2-2: Product: USB2.0-Serial
 [14791.172973] ch341 2-2:1.0: ch341-uart converter detected
 [14791.187657] usb 2-2: ch341-uart converter now attached to ttyUSB0

Mark

---

