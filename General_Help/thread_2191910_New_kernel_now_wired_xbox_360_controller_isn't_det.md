---
title: "New kernel now wired xbox 360 controller isn't detected anymore"
date: 2013-12-04
forum: General Help
---

### Post by dannyboy79 on 2013-12-04
I was running kernel 3.7.0-030700-generic but I want to use bcache which requires kernel 3.10 or later so I installed 3.10.1-031001-generic using a PPA, everything works except for some reason my wired xbox 360 controller no longer works within serious sam 3 bfe. it's not even detected within the game. it's also acting very weird with metro last light, the B button became the A button and the X button became the B button. i went into steam big picture mode and ensured my controller was setup correctly. i double checked and the xpad module is loaded. I had this controller working with all my games prior to installing this new kernel. is it possible that kernel 3.10 changed something with xpad because it is a built in kernel module. looking at my dmesg output after plugging it in i see the following
```
[16000.269252] usb 4-5: new full-speed USB device number 5 using ohci_hcd
[16000.445096] usb 4-5: New USB device found, idVendor=0e6f, idProduct=0213
[16000.445101] usb 4-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[16000.445103] usb 4-5: Product: Afterglow Gamepad for Xbox 360
[16000.445105] usb 4-5: Manufacturer: Performance Designed Products
[16000.445106] usb 4-5: SerialNumber: 05F79686
[16000.447185] input: Afterglow Gamepad for Xbox 360 as /devices/pci0000:00/0000:00:13.0/usb4/4-5/4-5:1.0/input/input19
```
Is there some xpad module config file or something I can check and see why this is occuring with a new kernel? I am going back to the last working controller kernel for now just so I can play my games the way I want with the wired xbox 360 controller BUT really need kernel 3.10 so I can implement bcache and use my OCZ Synapse Cache SSD drive

---

### Post by dannyboy79 on 2013-12-08
very weird! i went back to 3.7 kernel and everything is working again. controller is found within ss3 bfe and metro last light buttons are mapped correctly now also.

---

### Post by dannyboy79 on 2014-01-11
so i am still presented with this issue. just installed kernel 3.8.0-25 and now the controller is acting weird again, metro last light the buttons are mapped wrong. i just don't understand how a new kernel can mess up controller buttons? I even went back into steam big picture and remapped all the buttons but still isn't correct. Can any speculate as to why a new kernel would make a working xbox 360 wired controller act different?

---

### Post by dannyboy79 on 2014-09-09
this is still an issue. i don't get how Xubuntu 14.04, kernel 3.13.0-36-generic, Steam, and Metro: Last Light have something as simple as xbox 360 wired controller button mapping issues and it's not fixed. This makes no sense to me! I map all the buttons correctly in Big Picture mode within Steam yet when I fire up MLL all the buttons are messed up. I can't even play the game with a controller.

---

