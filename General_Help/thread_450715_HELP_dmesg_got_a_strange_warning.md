---
title: "HELP dmesg got a strange warning"
date: 2007-05-21
forum: General Help
---

### Post by vb2006 on 2007-05-21
Hi, I was following an howto for a bluetooth device, after installing some packages I typed dmesg to see if it was reconized and scrolling down I found these warning:

[COLOR="Red"]
[   48.126564] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
[   48.127570] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
[   48.128343] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it![/COLOR]

Can someone explain me what are these warnings and how can I fix them

Thanks very much for you help.

---

### Post by daller on 2007-05-21
It's a warning, not an error...
Your settings does not include the device settings for your graphics card!
I get that warning too... Nothing to be worried about! (if you have time to look through the whole dmesg output, youll probably find many warnings!)

---

### Post by vb2006 on 2007-05-21
Thanks very much, i feel better now

---

