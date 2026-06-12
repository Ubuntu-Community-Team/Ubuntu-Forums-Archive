---
title: "bluetooth in i3wm doesn't work unless connected in unity first"
date: 2016-01-09
forum: General Help
---

### Post by tigerstripedcat on 2016-01-09
ubuntu 15.10
i3: 4.11

When I reboot my machine and log directly into i3 I can't get bluetooth to connect to my headset.  It does pair (with bluetooth-wizard), but when I try to connect (with blueman-applet), I get:

Connection Failed: DBusFailedError: No such file or directory

When I try and remove the headset and repair I get:

Connect failed for /org/bluz/hci0/dev_B8_AD_3E_0A_AD_D2: GDBus. Error:org.bluez.Error.Failed: No such file or directory

However, when I log into unity first, and use the unity bluetooth applet to connect, it works fine. A couple of things:

* I'm not the only one having this problem: [https://faq.i3wm.org/question/2659/having-to-log-in-with-unity-first-to-link-with-a-bluetooth-device.1.html](https://faq.i3wm.org/question/2659/having-to-log-in-with-unity-first-to-link-with-a-bluetooth-device.1.html)
* It seems that unity (or the applet) does something (creates some directories?) to connect that i3 alone is not

Any suggestions?
Thanks!

---

