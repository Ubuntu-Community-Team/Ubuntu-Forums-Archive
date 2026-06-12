---
title: "Any idea why my udev rule won't work?"
date: 2016-01-20
forum: General Help
---

### Post by wilk3sy on 2016-01-20
Hi all

After reading a couple of posts on here and here

[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

I decided to add the following rule 

> /etc/udev/rules.d/40-joysticks.rules 

> ATTRS{idVendor}=="1593", ATTRS{product}=="V0662NOoUxy", NAME="input/js0", MODE="0666"

The issue being the joysticks are coming in on /dev/hidraw0 and /dev/hidraw3 OR 6. So my aim was, working with one first, set it up as coming in on /dev/input/js0.

I thought it seemed simple enough after reading the documentation, but it turns out that's not the case. 

Thanks. 

Ben

---

