---
title: "Firefox displays faulty, streaky pictures"
date: 2013-08-16
forum: General Help
---

### Post by Nuc72 on 2013-08-16
Hi Guys,

I'm experiencing a bit strange behavior of Firefox recently: it displays faulty, streaky pictures quite often on webpages. This phenomenon started with version 22, actually I use v23. Please check these examples:
[http://ubuntuone.com/3LeVkh5UxHDXYATRifBFYC](http://ubuntuone.com/3LeVkh5UxHDXYATRifBFYC)
[http://ubuntuone.com/7V7uBHwmtgRZv7lZLjL40i](http://ubuntuone.com/7V7uBHwmtgRZv7lZLjL40i)
[http://ubuntuone.com/0BIlZPhVNwwCmk1q2esGwS](http://ubuntuone.com/0BIlZPhVNwwCmk1q2esGwS)
[http://ubuntuone.com/4N5CPrLv6EDdpnnLMwq9Uj](http://ubuntuone.com/4N5CPrLv6EDdpnnLMwq9Uj)
[http://ubuntuone.com/6xQvS74UhEeZlL68uLV2iZ](http://ubuntuone.com/6xQvS74UhEeZlL68uLV2iZ)

Does anybody know how to solve this problem?

Info:
Dell Inspiron N5010 Intel graphics
Freshly installed Xubuntu 13.04
Kernel 3.8.0-27 (64bit)
Xorg 1.13.3
No restricted drivers are in use
Firefox 23
FF Add-on: Speed Dial 0.9.6.15

---

### Post by Nuc72 on 2013-08-17
??

---

### Post by chkneater on 2013-08-17
Are you running Jack at the same time by any chance?

---

### Post by Nuc72 on 2013-08-17
No I'm not. :-(

---

### Post by Nuc72 on 2013-08-17
Just a supplement: there is no change if I turn off hardware acceleration.

---

### Post by Nuc72 on 2013-08-18
??

---

### Post by Nuc72 on 2013-08-18
I've tried to boot with Live CD: the issue is gone!
There is kernel 3.8.0-19 on Live CD, Firefox v20. I believe this issue is kernel related, so the solution is use kernel 3.8.0-19 or earlier.

---

### Post by Nuc72 on 2013-08-28
It seems kernel 3.8.0-29 solved the issue. :-)

---

