---
title: "Can't get Microsoft Arc Touch Mouse Surface Edition to pair with ubuntu 15.10"
date: 2015-11-08
forum: General Help
---

### Post by mitch17 on 2015-11-08
Ubuntu 15.10 should have bluez5, and allow you to connect low-energy bluetooth devices, correct?

I cannot get my arc mouse to connect. It is discoverable, and will pair, but will only show "paired" when it is put in discovery mode. When it is taken out of discovery mode it shows it is no longer paired.

Using blueman / default bluetooth manager.

Help?

---

### Post by mitch17 on 2015-11-08
bump

---

### Post by mitch17 on 2015-11-09
Anybody using one of these mice? Or is this mouse not compatible with ubuntu / linux?

---

### Post by Hiro._Sasaki on 2015-11-10
I'm using it .

I was not used by the same thing.
Please try bluetoothctl cmd.

But,,,,
disconnected often. everytime
# hciconfig hci0 reset


15.04 + Bluez5.x I had used without a problem .

---

### Post by jimmux on 2015-11-17
I got it working with help from this [bug report]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1510570?comments=all").

Note that it wasn't instantly fixed. I had to restart before it would pair, then restart again for the mouse to actually work.

---

