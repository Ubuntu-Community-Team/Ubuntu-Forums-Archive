---
title: "USB Question"
date: 2007-12-05
forum: General Help
---

### Post by shanerdaner on 2007-12-05
I have a question about USB.  I bought a laptop cooling pad that runs on a usb connection.  This has 4 extra ports..  The ports can read my sd card however it cannot seem to run my portable hd  is this due to it not producing enough power?  when I plug the drive in directly it works fine.  Just curious.. a geek like me just wants to know!!!!!!!  My ext hdd runs off of USB power only its a wd 120 gb...thanks!

---

### Post by rexxxlo on 2007-12-05
yes you are orrect if it does not have an acpower supply and the chill mat draws too much other components ill not work the usb header can not supply much current im not sure how much but it isnt much

get a powered usb hub  something similar to this

[http://www.amazon.com/Belkin-4-Port-Cable-Power-Supply/dp/B00004Z6KW](http://www.amazon.com/Belkin-4-Port-Cable-Power-Supply/dp/B00004Z6KW)

---

### Post by geraldm on 2007-12-06
If your usbfs is mounted, and you have a /proc/bus/usb/devices file, then you have the information that you need in there.  
For each device, its various configurations provide the 
maximum power that is used by the device.  It is in the line beginning C:, but you need to use
the active configuration, which should have "C:*".  The total for all devices from 1 hub port
cannot exceed 500ma by USB standards; the device is required to draw no more than 100ma until its configuration is selected.  If the total power used exceeds 500ma, then the device is not to be made active, and must remain inactive.  The various usb ports monitor this in hardware, and excessive power drain would be detected in hardware and shut down (old passive hubs do not do detection, but the port that the passive hub is connected to must.)

Gerald

---

### Post by shanerdaner on 2007-12-06
> **geraldm said:**
> If your usbfs is mounted, and you have a /proc/bus/usb/devices file, then you have the information that you need in there.  
For each device, its various configurations provide the 
maximum power that is used by the device.  It is in the line beginning C:, but you need to use
the active configuration, which should have "C:*".  The total for all devices from 1 hub port
cannot exceed 500ma by USB standards; the device is required to draw no more than 100ma until its configuration is selected.  If the total power used exceeds 500ma, then the device is not to be made active, and must remain inactive.  The various usb ports monitor this in hardware, and excessive power drain would be detected in hardware and shut down (old passive hubs do not do detection, but the port that the passive hub is connected to must.)

Gerald

ok well it sounds like I cannot draw enough juice to spin the hdd that is very interesting i did not know that.  my next question is what would cause a usb to quit working?  it still has power however it does not read any devices.  including a printer.
thanks for all of the info!!

---

### Post by geraldm on 2007-12-06
Your answer should be in your log file, /var/log/syslog, if the device does not work.
If you are having any trouble with a particular device, it is best to test with as few devices as 
possible, even with just the port on the computer and just the one device.  

Gerald

---

### Post by shanerdaner on 2007-12-06
> **geraldm said:**
> Your answer should be in your log file, /var/log/syslog, if the device does not work.
If you are having any trouble with a particular device, it is best to test with as few devices as 
possible, even with just the port on the computer and just the one device.  

Gerald
ok ty for your help!

---

