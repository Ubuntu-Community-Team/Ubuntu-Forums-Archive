---
title: "Fingerprint reader for Linux."
date: 2013-09-05
forum: General Help
---

### Post by odror on 2013-09-05
Hi

My new Hp laptop ( TouchSmart 17t-j000) comes with fingerprint detection for unlocking passwords. Does anyone knows if there is a driver/app for Linux.


Thanks

---

### Post by jrda on 2013-09-06
Yes, there is FPrint - [http://wiki.ubuntuusers.de/fprint](http://wiki.ubuntuusers.de/fprint)
[http://www.freedesktop.org/wiki/Software/fprint/](http://www.freedesktop.org/wiki/Software/fprint/)

---

### Post by emdeem on 2013-09-06
[https://launchpad.net/~fingerprint/+archive/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/fingerprint-gui)

[http://www.n-view.net/Appliance/fingerprint/](http://www.n-view.net/Appliance/fingerprint/)

---

### Post by odror on 2013-09-08
> **jrda said:**
> Yes, there is FPrint - [http://wiki.ubuntuusers.de/fprint](http://wiki.ubuntuusers.de/fprint)
[http://www.freedesktop.org/wiki/Software/fprint/](http://www.freedesktop.org/wiki/Software/fprint/)

I have tried that, But I get No device found when using fprint-demo. The device that I have as listed on windows is: Validity Sensors (WBF) (PID=0050)
When I do lsusb I get > Bus 003 Device 006: ID 138a:0050 Validity Sensors, Inc.  So it is clearly detected.

---

### Post by jrda on 2013-09-08
Seems like fprint doesn't support your Device.

What about FingerprintGUI?

---

### Post by odror on 2013-09-09
> **jrda said:**
> Seems like fprint doesn't support your Device.

What about FingerprintGUI?

There is no FingerprintGUI for 13.10. I installed the one for 13.04. It did not detect my device, but it listed the USB devices, My device was listed too as unknown device. It did not let me select it.

---

### Post by jrda on 2013-09-09
FingerprintGUI doesn't support your Device 

> Supported readers (run command lsusb to find out the ID of your reader)
============
     045e:00bb    08ff:1683    08ff:2580    08ff:268d
     045e:00bc    08ff:1684    08ff:2660    08ff:268e
     045e:00bd    08ff:1685    08ff:2680    08ff:268f
     045e:00ca    08ff:1686    08ff:2681    08ff:2691
     0483:2015    08ff:1687    08ff:2682    08ff:2810
     0483:2016    08ff:1688    08ff:2683    08ff:5501
     05ba:0007    08ff:1689    08ff:2684    08ff:5731
     05ba:0008    08ff:168a    08ff:2685    138a:0001
     05ba:000a    08ff:168b    08ff:2686    138a:0005
     061a:0110    08ff:168c    08ff:2687    138a:0008
     08ff:1600    08ff:168d    08ff:2688    147e:1000
     08ff:1660    08ff:168e    08ff:2689    147e:2016
     08ff:1680    08ff:168f    08ff:268a    147e:2020
     08ff:1681    08ff:2500    08ff:268b    147e:3001
     08ff:1682    08ff:2550    08ff:268c    1c7a:0603
and
     0483:2015    147e:1003    147e:3000
     0483:2016    147e:2015    147e:3001
     147e:1000    147e:2016    147e:5002
     147e:1001    147e:2020    147e:5003



:(

---

### Post by odror on 2013-09-09
Is there a way to get my device supported. Other devices by the same vendor are supported. Can the code  be modified to accept my ID.

---

### Post by jrda on 2013-09-09
I think you should contact the maintainers:

[https://bugs.freedesktop.org/enter_bug.cgi?product=libfprint](https://bugs.freedesktop.org/enter_bug.cgi?product=libfprint)
[http://darkblue.homeip.net/fingerprint/Forum/](http://darkblue.homeip.net/fingerprint/Forum/)
[http://darkblue.homeip.net/fingerprint/Forum/topic.php?TopicId=340&Posts=1](http://darkblue.homeip.net/fingerprint/Forum/topic.php?TopicId=340&Posts=1)

---

### Post by payden on 2014-01-05
I'm working on a libfprint driver for this device.  

[http://paydensutherland.com/2014/01/libfprint-138a-0050-driver/](http://paydensutherland.com/2014/01/libfprint-138a-0050-driver/)

---

