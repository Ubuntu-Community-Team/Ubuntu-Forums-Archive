---
title: "Delcom USB HID Programable Triple Button Switch"
date: 2013-12-19
forum: General Help
---

### Post by prakava on 2013-12-19
Hi everyone,

I am trying to use a USB HID Programable Triple Button Switch by Delcom. More details here - [http://www.delcomproducts.com/productdetails.asp?PartNumber=706503-F-5M](http://www.delcomproducts.com/productdetails.asp?PartNumber=706503-F-5M)

I need to find a way to use this device to open a file when I press a particular switch. 

I do read the device at /dev/usb/hiddev0

The need is to read the device and a specific input from it. 
hexdump - C /dev/hidraw seems to not respond at all.

I tried less -f /dev/usb/hiddev0 and the terminal just freezes. Any help in the right direction would be appreciated. Thanks.[COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR]

Thanks.

---

