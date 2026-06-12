---
title: "how do I know my modem serial device name"
date: 2008-05-11
forum: General Help
---

### Post by Green_Star on 2008-05-11
I am trying to use efax-gtk, and I got following error when I try to see whether modem working or not, (by pressing 'standby' button)

efax-0.9a: 07:28:31 opened /dev/ttyS1
efax-0.9a: 07:28:37 sync: dropping DTR
efax-0.9a: 07:28:42 sync: sending escapes
efax-0.9a: 07:28:47 Error: sync: modem not responding
efax-0.9a: 07:28:47 finished - no response from modem


I guess I am not using correct serial device, how do I know what is my modem serial port?

---

### Post by housam on 2008-05-11
Try to use the [[COLOR="Red"]_ScanModem_[/COLOR]]("http://132.68.73.235/linmodems/index.html#scanmodem") tool. it'll give you infos about your modem

---

### Post by Green_Star on 2008-05-12
thanks for helping me,

I installed drivers from 

[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)
[http://linux.dell.com/files/ubuntu/gutsy/modem-drivers/hsf/](http://linux.dell.com/files/ubuntu/gutsy/modem-drivers/hsf/)

Looks like these free drivers do not support FAX, is there any other way to use my modem for faxing?

---

