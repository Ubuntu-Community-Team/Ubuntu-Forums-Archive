---
title: "force usb to use same dev id using udev rule"
date: 2012-10-31
forum: General Help
---

### Post by srikanth007m on 2012-10-31
I need some help regarding the usb devices(Android based smartphones), more over i am new to linux. After googling a lot i heard there is trick using udev rule. Does this udev rule solved my problem? 

how to create a rule for my below problem. Any help would really helpful..

I am testing some android based mobiles in linux machine. The automation script uses the device id under "/dev/bus/usb/001/"053" it will be always under bus 001 only.. But the dev id will be random like if i insert one mobile then the dev id will be 053, if remove and insert it again then the dev id will be 054..

The problem is, when some tests runs on the device and if device gets rebooted then new dev id is showing for the rebooted one and my scripts failing due to new dev id..

Is there any way to force usb devices to use same dev id instead of new one. So that there will be no issues to my tests even after device reboots.

Thanks in advance.

---

