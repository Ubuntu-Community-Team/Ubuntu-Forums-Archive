---
title: "scanner not detected"
date: 2016-04-30
forum: General Help
---

### Post by stephenbbb on 2016-04-30
on Ubuntu 14.01 I have sane and edited the [B]/etc/sane.d/xerox_mfp.conf file 
adding 
[I]# Samsung SCX-3400
usb 0x04e8 0x344f

and 
[/I][/B]/lib/udev/rules.d/40-libsane.rules

adding

 # Samsung SCX-3400
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="344f", ENV{libsane_matched}="yes"

sane-find-scanner finds nothing.
[B]
[/B]

---

### Post by kurt18947 on 2016-04-30
Have you looked at this?

[http://www.samsung.com/my/support/model/SCX-3400/XSS](http://www.samsung.com/my/support/model/SCX-3400/XSS)

Samsung seems pretty good with their linux support. I use that same driver - it appears to support many or most Samsung machines - and it works well with a network connected machine. I'm not sure if your manual editing of the libsane.rules file will cause problems or not. If the Samsung driver does not work, I'd consider deleting those lines.

---

